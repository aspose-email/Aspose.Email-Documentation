---
title: "Trabajando con Mensajes del Servidor"
url: /es/java/working-with-messages-from-server/
weight: 50
type: docs
---

## **Obteniendo Información de la Bandeja de Entrada**

Podemos obtener información sobre la bandeja de entrada, como el número de mensajes y el tamaño de la bandeja de entrada utilizando los métodos [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) y [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

- El método [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) devuelve el tamaño de la bandeja de entrada en bytes.
- El método [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) devuelve un objeto del tipo [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

También es posible obtener el número de mensajes utilizando la propiedad [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) y el tamaño utilizando la propiedad [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) de la clase [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/). El siguiente código de muestra muestra cómo obtener información sobre la bandeja de entrada. Muestra cómo:

1. Crear un [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Conectar a un servidor POP3.
1. Obtener el tamaño de la bandeja de entrada.
1. Obtener información de la bandeja de entrada.
1. Obtener el número de mensajes en la bandeja de entrada.
1. Obtener el tamaño ocupado.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Especificar host, nombre de usuario, contraseña, puerto y opciones de seguridad para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Obtener el tamaño de la bandeja de entrada, obtener información de la bandeja de entrada, número de mensajes en la bandeja de entrada
long nSize = client.getMailboxSize();
System.out.println("El tamaño de la bandeja de entrada es " + nSize + " bytes.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("El número de mensajes en la bandeja de entrada es " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("El tamaño ocupado es " + nOccupiedSize);
~~~

## **Obteniendo el Conteo de Correos en la Bandeja de Entrada**

El siguiente código muestra cómo contar los mensajes de correo electrónico en una bandeja de entrada.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Conteo de mensajes: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Error:" + ex.toString());
}
~~~

Aspose.Email permite a los desarrolladores trabajar con correos electrónicos de muchas maneras diferentes. Por ejemplo, pueden recuperar información del encabezado antes de decidir si descargar un correo electrónico. O pueden recuperar correos electrónicos de un servidor y guardarlos sin analizarlos (más rápido) o después de analizarlos (más lento). Este artículo muestra cómo recuperar y convertir correos electrónicos.

## **Recuperando Información de Encabezados de Correo Electrónico**

Los encabezados de correo electrónico pueden darnos información sobre un mensaje de correo electrónico que podemos usar para decidir si recuperar o no todo el mensaje de correo electrónico. Normalmente, la información del encabezado contiene el remitente, el asunto, la fecha de recepción, etc. (Los encabezados de correo electrónico se describen en detalle en [Personalizando Encabezados de Correo Electrónico](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). Ese tema trata específicamente sobre cómo enviar un correo electrónico con SMTP, pero la información del contenido del encabezado de correo electrónico sigue siendo válida para correos electrónicos POP3). Los siguientes ejemplos muestran cómo recuperar encabezados de correo electrónico de un servidor POP3 por el número de secuencia del mensaje.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especificar host, nombre de usuario, contraseña, puerto y opciones de seguridad para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Mostrar clave y valor en la colección de encabezados
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

## **Recuperando Mensajes de Correo Electrónico**

La clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona la capacidad de recuperar mensajes de correo electrónico del servidor POP3 y analizarlos en una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) con la ayuda de los componentes [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) contiene varias propiedades y métodos para manipular el contenido de los correos electrónicos. Utilizando el método [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), puedes obtener una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) directamente del servidor POP3. El siguiente código muestra cómo recuperar un mensaje de correo electrónico completo del servidor POP3.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especificar host, nombre de usuario, contraseña, puerto y opciones de seguridad para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Crear una instancia de la clase MailMessage y recuperar el mensaje
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("De:" + message.getFrom());
        System.out.println("Asunto:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperando Información de Resumen del Mensaje utilizando Identificación Única**

El cliente POP3 de la API puede recuperar información de resumen de mensajes del servidor utilizando la identificación única del mensaje. Esto proporciona acceso rápido a la información breve del mensaje sin primero recuperar el mensaje completo del servidor. El siguiente código muestra cómo recuperar la información de resumen del mensaje.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "identificación única de un mensaje del servidor";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~

## **Listando Mensajes con MultiConexión**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-) que se puede usar para crear múltiples conexiones para operaciones pesadas. También puedes establecer la cantidad de conexiones que se utilizarán durante el modo de multiconexión utilizando [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). El siguiente código demuestra el uso del modo de multiconexión para listar mensajes y compara su rendimiento con el modo de conexión única.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de la clase Pop3Client
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

System.out.println("multiConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Relación de Rendimiento: " + performanceRelation);
~~~

{{% alert color="primary" %}} 

Por favor, tenga en cuenta que el uso del modo de multiconexión no garantiza un aumento de rendimiento.

{{% /alert %}} 

## **Recuperando Mensajes del Servidor y Guardando en Disco**

### **Guardar Mensaje en Disco sin Analizar**

Si deseas descargar mensajes de correo electrónico del servidor POP3 sin analizarlos, utiliza la función [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). La función [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) no analiza el mensaje de correo electrónico, por lo que es más rápida que la función [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-). El siguiente código muestra cómo guardar un mensaje por su número de secuencia, en este caso, el número 1. El método [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) guarda el mensaje en el formato original EML sin analizarlo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Crear una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especificar host, nombre de usuario, contraseña, puerto y opciones de seguridad para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Guardar mensaje en disco por número de secuencia del mensaje
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Mensajes de correo electrónico recuperados utilizando POP3 ");
~~~

### **Analizar Mensaje Antes de Guardar**

El siguiente código utiliza el método [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) de [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) para recuperar un mensaje de un servidor POP3 por su número de secuencia, luego guarda el mensaje en disco utilizando el asunto como el nombre del archivo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "pop3/";

// Crear una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especificar host, nombre de usuario y contraseña, puerto y opciones de seguridad para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Recuperar el mensaje por su número de secuencia y guardar el mensaje utilizando su asunto como el nombre del archivo
    MailMessage msg = client.fetchMessage(1);
    msg.save(dataDir + "first-message_out.eml", SaveOptions.getDefaultEml());
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Recuperando Mensajes en Grupo**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) proporciona un método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) que acepta un iterable de Números de Secuencia o ID Únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El siguiente código demuestra el uso del método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) para recuperar mensajes por Números de Secuencia y ID Únicos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de la clase Pop3Client
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("Conteo de ListMessages: " + messageInfoCol.size());

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

## **Filtrando Mensajes por Remitente, Destinatario o Fecha**

La clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), descrita en [Conectando a un Servidor POP3](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), proporciona el método [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) que obtiene todos los mensajes de una bandeja de entrada. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) que toma [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. La clase [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) proporciona varias propiedades para especificar las condiciones de la consulta, por ejemplo, fecha, asunto, remitente, destinatario, etc. La clase [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) se utiliza para construir la expresión de búsqueda. Primero, se establecen todas las condiciones y restricciones y luego [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) se llena con la consulta desarrollada por [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). El objeto de clase [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) es utilizado por [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) para extraer la información filtrada del servidor. Este artículo muestra cómo filtrar mensajes de correo electrónico de una bandeja de entrada. El primer ejemplo ilustra cómo filtrar mensajes en función de una fecha y un asunto. También mostramos cómo filtrar por otros criterios y cómo construir consultas más complejas. También se muestra la aplicación de los filtros de Fecha y Hora para recuperar correos electrónicos específicos de la bandeja de entrada. Además, también se muestra cómo aplicar filtros que distinguen entre mayúsculas y minúsculas.

### **Filtrando Mensajes de la Bandeja de Entrada**

Para filtrar mensajes de una bandeja de entrada:

1. [Conéctate e inicia sesión en un servidor POP3](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Crea una instancia de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) y establece las propiedades deseadas.
1. Llama al método [Pop3Client.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) y pasa el [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parámetros para obtener solo los mensajes filtrados.

El siguiente código muestra cómo conectarse a una bandeja de entrada POP3 y obtener mensajes que llegaron hoy y tienen la palabra "newsletter" en el asunto.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Conectarse e iniciar sesión en POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Establecer condiciones, Asunto contiene "Newsletter", Correos que llegaron hoy
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Construir la consulta y obtener la lista de mensajes
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " mensaje(s) encontrados.");
~~~ 

### **Obteniendo Mensajes que Cumplen Criterios Específicos**

[Los ejemplos de código anteriores](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) filtran mensajes en función del asunto del correo electrónico y la fecha. Podemos utilizar otras propiedades para establecer otras condiciones soportadas. A continuación se presentan algunos ejemplos de cómo configurar las condiciones usando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

Los siguientes fragmentos de código muestran cómo filtrar correos electrónicos según otros criterios:

- Encontrar correos electrónicos entregados hoy.
- Encontrar correos electrónicos recibidos dentro de un rango.
- Encontrar correos electrónicos de un remitente específico.
- Encontrar correos electrónicos enviados desde un dominio específico.
- Encontrar correos electrónicos enviados a un destinatario específico.

#### **Fecha de Hoy**

El siguiente código muestra cómo encontrar correos electrónicos entregados hoy.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Correos que llegaron hoy
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~ 

#### **Rango de Fechas**

El siguiente código muestra cómo encontrar correos electrónicos recibidos dentro de un rango.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Correos que llegaron en los últimos 7 días
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~ 

#### **Remitente Específico**

El siguiente código muestra cómo encontrar correos electrónicos de un remitente específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos electrónicos de un remitente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~ 

#### **Dominio Específico**

El siguiente código muestra cómo encontrar correos electrónicos enviados desde un dominio específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos electrónicos de un dominio específico
builder.getFrom().contains("SpecificHost.com");
~~~ 

#### **Destinatario Específico**

El siguiente código muestra cómo encontrar correos electrónicos enviados a un destinatario específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos electrónicos enviados a un destinatario específico
builder.getTo().contains("recipient");
~~~ 

### **Construyendo Consultas Complejas**

Si diferentes propiedades de [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) se establecen en declaraciones separadas, entonces se cumplirán todas las condiciones. Por ejemplo, si queremos obtener mensajes entre un rango de fechas y de un host específico, necesitamos escribir tres declaraciones.

#### **Combinando Consultas con AND**

El siguiente código muestra cómo combinar consultas con AND.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Correos de un host específico, obtener todos los correos que llegaron antes de hoy y todos los correos que llegaron desde hace 7 días
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~ 

#### **Combinando Consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) proporciona el método [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) que toma dos instancias de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parámetros. Obtiene los mensajes que coinciden con cualquiera de las dos condiciones especificadas. El siguiente código muestra cómo filtrar mensajes que tengan "test" en el asunto o "noreply@host.com" como el remitente. El siguiente código muestra cómo combinar consultas con OR.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Especificar condición OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~ 

#### **Aplicando Filtros Sensibles a Mayúsculas y Minúsculas**

La API también proporciona la capacidad de filtrar correos electrónicos de la bandeja de entrada en función de un criterio sensible a mayúsculas y minúsculas. Los siguientes métodos ofrecen la capacidad de buscar correos electrónicos especificando el indicador de sensibilidad a mayúsculas y minúsculas.

- Método StringComparisonField.contains(String value, boolean ignoreCase)
- Método StringComparisonField.equals(String value, boolean ignoreCase)
- Método StringComparisonField.notContains(String boolean, bool ignoreCase)
- Método StringComparisonField.notEquals(String boolean, bool ignoreCase)

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase es Verdadero
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~