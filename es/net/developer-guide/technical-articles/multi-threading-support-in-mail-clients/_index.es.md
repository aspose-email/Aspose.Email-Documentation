---
title: "Soporte de múltiples hilos en los clientes de correo"
url: /es/net/multi-threading-support-in-mail-clients/
weight: 250
type: docs
---


Los clientes de correo como ImapClient y Pop3Client permiten a los usuarios utilizarlos en un entorno de múltiples hilos. Los clientes de correo permiten tener una o más conexiones con un servidor. Para gestionar un conjunto de conexiones dentro de los clientes se utiliza un grupo de conexiones. La cantidad de conexiones que se pueden crear y utilizar al mismo tiempo está limitada por la propiedad CredentialsByHostClient.MaxConnectionsPerServer. Esta propiedad puede establecerse en 1 o un valor mayor. Por defecto, esta propiedad es igual a 10. Se ha implementado una cola de comandos para la conexión para soportar operaciones de múltiples hilos. Los comandos implementan las operaciones más simples definidas en el protocolo, tales como Noop, Authenticate, etc. El usuario puede iniciar la ejecución de una cantidad mayor de comandos que la cantidad de conexiones disponibles. Sin embargo, se ejecutarán únicamente cuando el cliente pueda crear una conexión para la operación.
## **Métodos de uso de clientes de correo en un entorno de múltiples hilos**
Los clientes de correo tienen el siguiente comportamiento:

**1.** En el caso de MaxConnectionsPerServer = 1, el cliente crea 1 conexión, realiza la autenticación y autorización. Esta conexión se mantiene en estado de trabajo hasta que el cliente sea desechado. Todas las operaciones de diferentes hilos se dirigen a una cola de comandos ubicada en la conexión principal.

**2.** En el caso de MaxConnectionsPerServer > 1, el cliente crea la cantidad necesaria de conexiones, realiza la autenticación y autorización para cada conexión. Una conexión se reserva como conexión principal. Esta conexión se mantiene en estado de trabajo hasta que el cliente sea desechado. Todas las demás conexiones se crean y desechan bajo demanda. La cantidad máxima de tales conexiones está definida por la propiedad MaxConnectionsPerServer, es decir, por ejemplo, si MaxConnectionsPerServer = 2, entonces una se reserva como conexión principal y la segunda conexión se utiliza como adicional para operaciones que se ejecutan en otros hilos. En consecuencia, si MaxConnectionsPerServer = 3, entonces la primera conexión se reserva como conexión principal, y otras dos conexiones se utilizan como adicionales para operaciones que se ejecutan en otros hilos. En caso de que llegue una nueva solicitud de conexión de un nuevo hilo, y todas las conexiones ya estén en uso, el cliente espera hasta que el número de conexiones utilizadas se reduzca. Este es un momento muy importante que aclara por qué el desecho correcto de las conexiones es tan importante.
## **Ejemplos**
El usuario puede ejecutar operaciones en diferentes hilos de varias maneras. Pueden dividirse en dos tipos:

**1.** El usuario utiliza métodos asíncronos (Begin/End) definidos en el cliente. En este caso, el cliente de correo lanza nuevos hilos cuando es necesario. En el cliente se implementa una cola de tareas (por favor, no confundirse con la cola de comandos en la conexión). La tarea puede ejecutarse si la conexión está disponible. Una vez que la cantidad de conexiones utilizadas se vuelve inferior al valor límite, el cliente crea una nueva conexión, crea un hilo para la tarea actual y ejecuta esta tarea. Ejemplo de uso de operaciones asíncronas:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmail.cs" >}}



**2.** El usuario puede crear hilos utilizando objetos como Thread, ThreadPool, Task o cualquier otro objeto destinado a este propósito. También el usuario puede usar hilos creados en código de terceros. Durante esto, el cliente tiene dos modelos de comportamiento

**a.** Si el usuario no ha tomado la creación de conexiones adicionales para operaciones en el hilo, todas las operaciones para este hilo se enviarán a la cola de comandos de la conexión principal. Un ejemplo de operaciones en un hilo adicional sin crear una nueva conexión, todas las transacciones se realizan a través de la conexión principal:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool.cs" >}}



**b.** Cuando el usuario ejecuta un método para crear una nueva conexión para el hilo adicional, este hilo está bloqueado hasta que el valor de cuota para nuevas conexiones se modifique para permitir una nueva conexión. Luego se crea una nueva conexión. Esta conexión se establece como la conexión predeterminada para todas las operaciones en este hilo. Después de que todas las operaciones en este hilo se completan, la conexión debe ser desechada. Para crear nuevas conexiones, use el método CredentialsByHostClient.CreateConnection. Este método devuelve un objeto que implementa la interfaz IDisposable. Para liberar la conexión, se debe invocar el método Dispose. La creación y el desecho de conexiones deben ejecutarse dentro del hilo donde se ejecutan las operaciones de correo. Intentar crear una nueva conexión en el hilo donde se ha creado el cliente de correo conduce a un error, porque este hilo en ese momento no puede usarse para la creación de una nueva conexión. También la creación de una nueva conexión no es posible cuando MaxConnectionsPerServer = 1. Un ejemplo de código para crear una nueva conexión en un hilo adicional:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-IMAP-SendIMAPasynchronousEmail-SendIMAPasynchronousEmailThreadPool1.cs" >}}
## **Recomendaciones**
Cabe señalar que si el usuario envía todos los comandos a la conexión principal, puede surgir una situación en la que los comandos de diferentes hilos se mezclen. El usuario debe entender qué comandos dependen de su secuencia, y tomar medidas para la sincronización de tales comandos. También es necesario considerar la posibilidad de ejecutar comandos en diferentes sesiones (IMAP/POP3). Las operaciones más que consumen tiempo, como FetchMessage, AppendMessage y Send, probablemente tienen sentido realizarlas con un nuevo hilo y una nueva conexión. Pero las operaciones rápidas como Delete tienen sentido realizarlas con la conexión principal. Tenga en cuenta que la inicialización de una nueva conexión es una operación que consume tiempo.