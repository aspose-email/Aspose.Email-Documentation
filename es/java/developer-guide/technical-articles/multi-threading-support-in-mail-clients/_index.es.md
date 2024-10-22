---
title: "Soporte para múltiples hilos en clientes de correo"
url: /es/java/multi-threading-support-in-mail-clients/
weight: 250
type: docs
---


Los clientes de correo como [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) y [Pop3Client](https://apireference.aspose.com/email/java/com.aspose.email/Pop3Client) permiten a los usuarios utilizarlos en un entorno de múltiples hilos. Los clientes de correo permiten tener una o más conexiones con un servidor. Para gestionar un conjunto de conexiones dentro de los clientes se utiliza un pool de conexiones. La cantidad de conexiones que se pueden crear y utilizar al mismo tiempo está limitada por la propiedad CredentialsByHostClient.MaxConnectionsPerServer. Esta propiedad puede ser establecida en 1 o un valor mayor. De forma predeterminada, esta propiedad es igual a 10. Se ha implementado una cola de comandos para la conexión para admitir operaciones de múltiples hilos. Los comandos implementan las operaciones más simples definidas en el protocolo, como Noop, Authenticate, etc. El usuario puede iniciar la ejecución de una cantidad mayor de comandos que la cantidad de conexiones disponibles. Pero se ejecutarán solo cuando el cliente pueda crear una conexión para la operación.

## **Métodos de uso de clientes de correo en un entorno de múltiples hilos**
Los clientes de correo tienen el siguiente comportamiento:

**1.** En el caso de MaxConnectionsPerServer = 1, el cliente crea 1 conexión, realiza la autenticación y autorización. Esta conexión se mantiene en estado de trabajo hasta el momento en que el cliente sea liberado. Todas las operaciones de diferentes hilos se dirigen a una cola de comandos ubicada en la conexión principal.

**2.** En el caso de MaxConnectionsPerServer > 1, el cliente crea la cantidad necesaria de conexiones, realiza la autenticación y autorización para cada conexión. Una conexión se reserva como conexión principal. Esta conexión se mantiene en estado de trabajo hasta el momento en que el cliente sea liberado. Todas las demás conexiones se crean y liberan bajo demanda. La cantidad máxima de tales conexiones está definida por la propiedad MaxConnectionsPerServer, es decir, por ejemplo, si MaxConnectionsPerServer = 2, entonces una se reserva como conexión principal, y la segunda conexión se utiliza como adicional para operaciones que se ejecutan en otros hilos. En consecuencia, si MaxConnectionsPerServer = 3, entonces la primera conexión se reserva como conexión principal, y otras dos conexiones se utilizan como adicionales para operaciones que se ejecutan en otros hilos. En caso de que llegue una nueva solicitud de conexión desde un nuevo hilo, y todas las conexiones ya estén en uso, el cliente espera hasta que el número de conexiones utilizadas no disminuya. Este es un momento muy importante que aclara por qué la liberación correcta de conexiones es tan importante.

## **Ejemplos**
El usuario puede ejecutar operaciones en diferentes hilos de varias maneras. Se pueden dividir en dos tipos:

**1.** El usuario utiliza métodos asíncronos (Begin/End) definidos en el cliente. En este caso, el cliente de correo lanza nuevos hilos cuando es necesario. En el cliente se implementa una cola de tareas (por favor, no confundir con la cola de comandos en la conexión). Una tarea puede ejecutarse si la conexión está disponible. Una vez que la cantidad de conexiones utilizadas se vuelve menor que el valor límite, el cliente crea una nueva conexión, crea un hilo para la tarea actual y ejecuta esta tarea. Ejemplo de uso de operaciones asíncronas:



~~~Java
// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");

ImapMessageInfoCollection messages = client.listMessages();
IAsyncResult res1 = client.beginFetchMessage(messages.get_Item(0).getUniqueId());
IAsyncResult res2 = client.beginFetchMessage(messages.get_Item(1).getUniqueId());
MailMessage msg1 = client.endFetchMessage(res1);
MailMessage msg2 = client.endFetchMessage(res2);
~~~



**2.** El usuario puede crear hilos utilizando objetos como Thread, ExecutorService o cualquier otro objeto destinado a este propósito. Además, el usuario puede utilizar hilos creados en código de terceros. Durante esto, el cliente tiene dos modelos de comportamiento

**a.** Si el usuario no ha tomado la creación de conexiones adicionales para operaciones en el hilo, todas las operaciones para este hilo se enviarán a la cola de comandos de la conexión principal. Un ejemplo de operaciones en un hilo adicional sin crear una nueva conexión, todas las transacciones se realizan a través de la conexión principal:



~~~Java
/**
 * Crea un servicio de ejecutor con un tamaño de pool fijo, que se 
 * agota después de un cierto período de inactividad.
 * 
 * @param poolSize El tamaño del pool básico y máximo
 * @param keepAliveTime El tiempo de mantenimiento activo
 * @param timeUnit La unidad de tiempo
 * @return El servicio de ejecutor
 */
private static ExecutorService createFixedTimeoutExecutorService(
    int poolSize, long keepAliveTime, TimeUnit timeUnit)
{
    ThreadPoolExecutor e = 
        new ThreadPoolExecutor(poolSize, poolSize,
            keepAliveTime, timeUnit, new LinkedBlockingQueue<Runnable>());
    e.allowCoreThreadTimeOut(true);
    return e;
}

final List<MailMessage> list = new ArrayList<MailMessage>();

ExecutorService executor = createFixedTimeoutExecutorService(1, 1000, TimeUnit.MILLISECONDS);

executor.execute(new Runnable() {
    public void run() {
        client.selectFolder("folderName");
        ImapMessageInfoCollection messageInfoCol = client.listMessages();
        for (ImapMessageInfo messageInfo : messageInfoCol) {
            list.add(client.fetchMessage(messageInfo.getUniqueId()));
        }
    }
});
~~~



**b.** Cuando el usuario ejecuta un método para crear una nueva conexión para un hilo adicional, este hilo se bloquea hasta que el valor de cuota para nuevas conexiones se modifique para permitir una nueva conexión. Luego se crea una nueva conexión. Esta conexión se establece como conexión predeterminada para todas las operaciones en este hilo. Después de que todas las operaciones en este hilo se completen, la conexión debe ser liberada. Para crear nuevas conexiones, utilice el método CredentialsByHostClient.CreateConnection. Este método devuelve un objeto que implementa la interfaz IDisposable. Para liberar la conexión, se debe invocar el método Dispose. La creación y liberación de la conexión deben ejecutarse dentro del hilo donde se ejecutan las operaciones de correo. Un intento de crear una nueva conexión en el hilo donde se ha creado el cliente de correo conduce a un error, porque este hilo en este momento no se puede utilizar para la creación de una nueva conexión. También la creación de una nueva conexión no es posible cuando MaxConnectionsPerServer = 1. Un ejemplo de código para crear una nueva conexión en un hilo adicional:


~~~Java
final List<MailMessage> list = new ArrayList<MailMessage>();

ExecutorService executor = createFixedTimeoutExecutorService(1, 1000, TimeUnit.MILLISECONDS);

executor.execute(new Runnable() {
    public void run() {
        IConnection connection = client.createConnection();
        try {
            client.selectFolder(connection, "FolderName");
            ImapMessageInfoCollection messageInfoCol = client.listMessages(connection);
            for (ImapMessageInfo messageInfo : messageInfoCol)
                list.add(client.fetchMessage(connection, messageInfo.getUniqueId()));
        } finally {
            connection.dispose();
        }
    }
});
~~~
## **Recomendaciones**
Cabe señalar que si el usuario envía todos los comandos a la conexión principal, puede surgir una situación en la que los comandos de diferentes hilos se mezclen. El usuario debe entender qué comandos dependen de su secuencia y tomar medidas para sincronizar dichos comandos. También es necesario considerar la posibilidad de ejecutar comandos en diferentes sesiones (IMAP/POP3). Las operaciones más que consumen tiempo, como FetchMessage, AppendMessage y Send. Probablemente tenga sentido realizar estas operaciones con un nuevo hilo y una nueva conexión. Pero las operaciones rápidas como Delete tienen sentido realizarlas con la conexión principal. Tenga en cuenta que la inicialización de una nueva conexión es una operación que consume mucho tiempo.