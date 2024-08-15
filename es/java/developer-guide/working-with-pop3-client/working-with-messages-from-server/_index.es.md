---
title: "Trabajando con mensajes del servidor"
url: /es/java/working-with-messages-from-server/
weight: 50
type: docs
---


## **Obtener información sobre el buzón**

Podemos obtener información sobre el buzón, como el número de mensajes y el tamaño del buzón, mediante el [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) and [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) métodos del [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.

- The [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) el método devuelve el tamaño del buzón en bytes.
- The [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) método devuelve un objeto de tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

También es posible obtener el número de mensajes mediante el [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) propiedad y el tamaño utilizando el [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) propiedad del [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/) clase. El siguiente código de ejemplo muestra cómo obtener información sobre el buzón. Muestra cómo:

1. Crea un [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Conéctese a un servidor POP3.
1. Obtenga el tamaño del buzón.
1. Obtenga información sobre el buzón.
1. Obtenga el número de mensajes del buzón.
1. Consigue el tamaño ocupado.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Get the size of the mailbox, Get mailbox info, number of messages in the mailbox
long nSize = client.getMailboxSize();
System.out.println("Mailbox size is " + nSize + " bytes.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("Number of messages in mailbox are " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("Occupied size is " + nOccupiedSize);
~~~

## **Obtener el recuento de correos electrónicos en el buzón**

El siguiente fragmento de código muestra cómo contar los mensajes de correo electrónico de un buzón.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Message count: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Error:" + ex.toString());
}
~~~

Aspose.Email permite a los desarrolladores trabajar con los correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar la información del encabezado antes de decidir si descargan un correo electrónico. O pueden recuperar los correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). En este artículo se muestra cómo recuperar y convertir correos electrónicos.

## **Recuperación de información de encabezados de correo electrónico**

Los encabezados de correo electrónico pueden proporcionarnos información sobre un mensaje de correo electrónico que podemos usar para decidir si queremos recuperar o no el mensaje de correo electrónico completo. Por lo general, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (los encabezados de los correos electrónicos se describen en detalle en [Personalización de encabezados de correo electrónico](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). Ese tema trata específicamente sobre el envío de un correo electrónico con SMTP, pero la información sobre el contenido del encabezado del correo electrónico sigue siendo válida (para los correos electrónicos POP3). En los siguientes ejemplos se muestra cómo recuperar los encabezados de correo electrónico de un servidor POP3 por el número de secuencia del mensaje.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Crea una instancia de the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username. password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Display key and value in the header collection
        System.out.print(headers.getKey(i));
        System.out.print(" : ");
        System.out.println(headers.get(i));
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperación de mensajes de correo electrónico**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) el componente de clase proporciona la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en un [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia con la ayuda de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) componentes. El [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase contiene varias propiedades y métodos para manipular el contenido del correo electrónico. Mediante el uso [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) método del [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) clase, puedes obtener un [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia directamente desde el servidor POP3. El siguiente fragmento de código muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Crea una instancia de the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Crea una instancia de the MailMessage class and Retrieve message
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("From:" + message.getFrom());
        System.out.println("Subject:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperación de la información resumida del mensaje mediante un identificador único**

El cliente POP3 de la API puede recuperar la información resumida del mensaje del servidor mediante el identificador único del mensaje. Esto proporciona un acceso rápido a la información breve del mensaje sin tener que recuperar primero el mensaje completo del servidor. El siguiente fragmento de código muestra cómo recuperar la información resumida del mensaje.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "unique id of a message from server";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~

## **Listar mensajes con MultiConnection**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). El siguiente fragmento de código muestra el uso del modo multiconexión para enumerar los mensajes y compara su rendimiento con el modo de conexión única.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Crea una instancia de the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

pop3Client.setConnectionsQuantity(5);
pop3Client.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol1 = pop3Client.listMessages();
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

pop3Client.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol2 = pop3Client.listMessages();
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

System.out.println("multyConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~

{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Obtener mensajes del servidor y guardarlos en el disco**

### **Guardar el mensaje en el disco sin analizarlo**

Si desea descargar mensajes de correo electrónico del servidor POP3 sin analizarlos, utilice el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) función. El [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) la función no analiza el mensaje de correo electrónico, por lo que es más rápida que [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) función. El siguiente fragmento de código muestra cómo guardar un mensaje por su número de secuencia, en este caso, el número 1. El [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) El método guarda el mensaje en el formato EML original sin analizarlo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Crea una instancia de the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Save message to disk by message sequence number
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Retrieved email messages using POP3 ");
~~~

### **Analiza el mensaje antes de guardarlo**

El siguiente fragmento de código usa el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) método para recuperar un mensaje de un servidor POP3 por su número de secuencia y, a continuación, guardar el mensaje en el disco con el asunto como nombre de archivo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";

// Crea una instancia de the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Fetch the message by its sequence number and Save the message using its subject as the file name
    MailMessage msg = client.fetchMessage(1);
    msg.save(dataDir + "first-message_out.eml", SaveOptions.getDefaultEml());
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Mensajes de búsqueda grupales**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona un [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) método que acepta números de secuencia iterables o ID únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) método para buscar mensajes por números de secuencia e ID único.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Crea una instancia de the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (Pop3MessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : pop3Client.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : pop3Client.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Filtrar mensajes por remitente, destinatario o fecha**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) clase, descrita en [Conexión a un servidor POP3](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), proporciona la [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) método que toma [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. El [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) La clase proporciona varias propiedades para especificar las condiciones de la consulta, por ejemplo, fecha, asunto, remitente, destinatario, etc. El [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) la clase se usa para construir la expresión de búsqueda. En primer lugar, se establecen todas las condiciones y restricciones y, a continuación [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) se rellena con la consulta desarrollada por [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). El [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) el objeto de clase es utilizado por [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) para extraer la información filtrada del servidor. En este artículo se muestra cómo filtrar los mensajes de correo electrónico de un buzón. El primer ejemplo ilustra cómo filtrar los mensajes en función de una fecha y un asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. También muestra la aplicación del filtro de fecha y hora para recuperar los correos electrónicos específicos del buzón. Además, también muestra cómo aplicar el filtrado que distingue entre mayúsculas y minúsculas.

### **Filtrar mensajes del buzón**

Para filtrar los mensajes de un buzón:

1. [Conectarse e iniciar sesión en un servidor POP3](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Crea una instancia de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) y defina las propiedades deseadas.
1. Llame al [pop3client.listMessages (consulta de MailQuery)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) método y pase el [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón POP3 y recibir los mensajes que llegaron hoy y que tienen la palabra «boletín» en el asunto.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Set conditions, Subject contains "Newsletter", Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " message(s) found.");
~~~

### **Recibir mensajes que cumplan con criterios específicos**

[Los ejemplos de código anteriores](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) filtra los mensajes según el asunto y la fecha del correo electrónico. También podemos usar otras propiedades para establecer otras condiciones compatibles. A continuación se muestran algunos ejemplos de cómo configurar las condiciones mediante [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

Los siguientes fragmentos de código muestran cómo filtrar los correos electrónicos según otros criterios:

- Encuentra los correos electrónicos enviados hoy.
- Busca los correos electrónicos recibidos dentro de un rango.
- Busca correos electrónicos de un remitente específico.
- Busca correos electrónicos enviados desde un dominio específico.
- Busca los correos electrónicos enviados a un destinatario específico.
 
#### **Fecha de hoy**

En el siguiente fragmento de código, se muestra cómo encontrar los correos electrónicos que se han entregado hoy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~

#### **Intervalo de fechas**

El siguiente fragmento de código muestra cómo buscar los correos electrónicos recibidos dentro de un rango.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Remitente específico**

El siguiente fragmento de código muestra cómo buscar correos electrónicos de un remitente específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

#### **Dominio específico**

El siguiente fragmento de código muestra cómo encontrar los correos electrónicos enviados desde un dominio específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~

#### **Destinatario específico**

El siguiente fragmento de código muestra cómo encontrar los correos electrónicos enviados a un destinatario específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~

### **Creación de consultas complejas**

Si es diferente [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) las propiedades se establecen en declaraciones separadas, entonces todas las condiciones coincidirían. Por ejemplo, si queremos recibir mensajes entre un intervalo de fechas y los de un anfitrión específico, necesitamos escribir tres declaraciones.

#### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Combinación de consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) proporciona la [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) método que requiere dos [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) instancias como parámetros. Obtiene los mensajes que cumplen cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar los mensajes que tienen la palabra «test» en el asunto o \"noreply@host.com\" como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

#### **Aplicar filtros que distinguen mayúsculas y minúsculas**

La API también ofrece la capacidad de filtrar los correos electrónicos del buzón según un criterio que distingue mayúsculas y minúsculas. Los siguientes métodos permiten buscar correos electrónicos especificando la distinción entre mayúsculas y minúsculas.

- Método StringComparisonField.contains (valor de cadena, booleano ignoreCase)
- Método StringComparisonField.equals (valor de cadena, booleano ignoreCase)
- Método StringComparisonField.notContains (String boolean, bool ignoreCase)
- Método StringComparisonField.noteQuals (String boolean, bool ignoreCase)

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~
