---
title: "Soporte de subprocesos múltiples en clientes de correo"
url: /es/net/multi-threading-support-in-mail-clients/
weight: 250
type: docs
---


Los clientes de correo como IMAPClient y Pop3Client permiten a los usuarios usarlos en entornos de subprocesos múltiples. Los clientes de correo permiten tener una o más conexiones con un servidor. Para administrar un conjunto de conexiones dentro de los clientes se utiliza el pool de conexiones. La cantidad de conexiones que se pueden crear y usar al mismo tiempo está limitada por la propiedad CredentialsByHostClient.maxConnectionsPerServer. Esta propiedad puede tener un valor igual o superior a 1. De forma predeterminada, esta propiedad es igual a 10. Se ha implementado una cola de comandos para que la conexión admita operaciones de subprocesos múltiples. Los comandos implementan las operaciones más simples definidas en el protocolo, como Noop, Authenticate, etc. El usuario puede iniciar la ejecución de una mayor cantidad de comandos que de conexiones disponibles. Pero solo se ejecutarán cuando el cliente pueda crear una conexión para la operación.
## **Métodos de uso de clientes de correo en un entorno de subprocesos múltiples**
Los clientes de correo electrónico tienen el siguiente comportamiento:

**1.** En el caso de MaxConnectionsPerServer = 1 cliente crea 1 conexión, realiza la autenticación y la autorización. Esta conexión se admite en estado de funcionamiento hasta el momento en que el cliente se dé de baja. Todas las operaciones de diferentes hilos se dirigen a una cola de comandos ubicada en la conexión principal.

**2.** En el caso de MaxConnectionsPerServer > 1, el cliente crea la cantidad necesaria de conexiones y realiza la autenticación y la autorización para cada conexión. Se reserva una conexión como conexión principal. Esta conexión se mantiene en estado de funcionamiento hasta el momento en que el cliente se deshaga de ella. Todas las demás conexiones se crean y eliminan a pedido. La cantidad máxima de conexiones de este tipo viene definida por la propiedad MaxConnectionsPerServer, es decir, si MaxConnectionsPerServer = 2, una se reserva como conexión principal y la segunda conexión se utiliza como conexión adicional para las operaciones que se ejecutan en otros subprocesos. En consecuencia, si MaxConnectionsPerServer = 3, la primera conexión se reserva como conexión principal y las otras dos conexiones se utilizan como adicionales para las operaciones que se ejecutan en otros hilos. En caso de que la próxima solicitud de conexión desde un nuevo subproceso llegue y todas las conexiones ya estén en uso, el cliente esperará hasta que el número de conexiones utilizadas no disminuya. Este es un momento muy importante que aclara por qué es tan importante disponer correctamente de las conexiones.
## **Examples**
El usuario puede ejecutar operaciones en diferentes subprocesos de varias maneras. Se pueden dividir en dos tipos:

**1.** El usuario usa métodos asincrónicos (inicio/final) definidos en el cliente. En este caso, el cliente de correo lanza nuevos hilos cuando es necesario. En el cliente está implementada la cola de tareas (por favor, no la confundas con la cola de comandos en conexión). La tarea se puede ejecutar si la conexión está disponible. Una vez que la cantidad de conexiones utilizadas sea inferior al valor límite, el cliente crea una nueva conexión, crea un hilo para la tarea actual y ejecuta esta tarea. Ejemplo de uso de operaciones asincrónicas:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmail.cs" >}}



**2.** El usuario puede crear hilos utilizando objetos como Thread, ThreadPool, Task o cualquier otro objeto para este propósito. Además, el usuario puede usar hilos creados con código de terceros. Durante este tiempo, el cliente tiene dos modelos de comportamiento

**a.** Si el usuario no ha iniciado la creación de conexiones adicionales para las operaciones del subproceso, todas las operaciones de este subproceso se enviarán a la cola de comandos de la conexión principal. Este es un ejemplo de operaciones en un hilo adicional sin crear una conexión nueva. Todas las transacciones se realizan a través de la conexión principal:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool.cs" >}}



**b.** Cuando el usuario ejecuta el método para crear una nueva conexión para un subproceso adicional, este subproceso se bloquea hasta que se cambie el valor de cuota para las nuevas conexiones para permitir una nueva conexión. Luego se crea una nueva conexión. Esta conexión se establece como conexión predeterminada para todas las operaciones de este hilo. Una vez completadas todas las operaciones de este hilo, la conexión debe desecharse. Para crear nuevas conexiones, utilice el método CredentialsByHostClient.createConnection. Este método devuelve un objeto que implementa la interfaz IDisposable. Para liberar la conexión, se debe invocar el método Dispose. La conexión de creación y eliminación debe ejecutarse dentro del subproceso donde se ejecutan las operaciones de correo. Al intentar crear una nueva conexión en el hilo en el que se creó el cliente de correo se produce un error, ya que este hilo en este momento no se puede utilizar para crear una nueva conexión. Además, no es posible crear una nueva conexión cuando maxConnectionsPerServer = 1. Un ejemplo de código de cómo crear un nuevo hilo adicional de conexión:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool1.cs" >}}
## **Recommendations**
Vale la pena señalar que si el usuario envía todos los comandos a la conexión principal, puede surgir una situación en la que se mezclen los comandos de diferentes subprocesos. El usuario debe comprender qué comandos dependen de su secuencia y tomar medidas para la sincronización de dichos comandos. También es necesario considerar la posibilidad de ejecutar comandos en diferentes sesiones (IMAP/POP3). Las operaciones que consumen más tiempo, como fetchMessage, AppendMessage y Send. Probablemente tenga sentido realizar estas operaciones con un nuevo hilo y una nueva conexión. Pero las operaciones rápidas como Eliminar tienen sentido realizarlas con la conexión principal. Tenga en cuenta que la inicialización de una nueva conexión es una operación que lleva bastante tiempo.
