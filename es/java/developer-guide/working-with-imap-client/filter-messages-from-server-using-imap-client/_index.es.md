---
title: "Filtrar mensajes del servidor usando cliente IMAP"
url: /es/java/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---

La [Clase ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona el [método listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el [método sobrecargado listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) que toma [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. La [clase MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) proporciona varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar mensajes basados en la fecha y el asunto. También mostramos cómo filtrar por otros criterios y cómo construir consultas más complejas. La API también proporciona la capacidad de aplicar criterios de búsqueda sensibles a mayúsculas y minúsculas para coincidir con criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar mensajes desde el buzón.

## **Filtrando Mensajes desde el Buzón**

1. [Conéctate e inicia sesión en un servidor IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Crea una instancia de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) y establece las propiedades.
1. Llama al [método ImapClient.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages-com.aspose.email.MailQuery-) y pasa el [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código te muestra cómo conectarte a un buzón IMAP y obtener mensajes que llegaron hoy y tienen la palabra "newsletter" en el asunto.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e iniciar sesión en IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Establecer condiciones, Asunto contiene "Newsletter", Correos que llegaron hoy
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Construir la consulta y obtener la lista de mensajes
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " mensaje(s) encontrado(s).");
// Desconectar de IMAP
client.dispose();
~~~

## **Obtener Mensajes que Cumplen Criterios Específicos**

[Los ejemplos de código anteriores](#filtering-messages-from-mailbox) filtran mensajes basados en el asunto del correo y la fecha. También podemos usar otras propiedades para establecer otras condiciones admitidas. A continuación se presentan algunos ejemplos de establecer condiciones utilizando [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Los fragmentos de código que siguen muestran cómo filtrar correos en:

1. La fecha de hoy.
1. Un rango de fechas.
1. De un remitente específico.
1. De un dominio específico.
1. De un destinatario específico.

### **Fecha de Hoy**

El siguiente fragmento de código te muestra cómo filtrar correos en la Fecha de Hoy.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Correos que llegaron hoy
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~
### **Rango de Fechas**
El siguiente fragmento de código te muestra cómo filtrar correos en el rango de fechas.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Correos que llegaron en los últimos 7 días
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Remitente Específico**

El siguiente fragmento de código te muestra cómo filtrar correos de un remitente específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos de un remitente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

### **Dominio Específico**

El siguiente fragmento de código te muestra cómo filtrar correos de un dominio específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos de un dominio específico
builder.getFrom().contains("SpecificHost.com");
~~~

### **Destinatario Específico**

El siguiente fragmento de código te muestra cómo filtrar correos hacia un destinatario específico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Obtener correos enviados a un destinatario específico
builder.getTo().contains("recipient");
~~~

## **Construyendo Consultas Complejas**

Si diferentes propiedades de [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) se establecen en declaraciones separadas, entonces todas las condiciones se emparejarían. Por ejemplo, si queremos obtener mensajes entre un rango de fechas y de un host específico, necesitamos escribir tres declaraciones.

### **Combinando Consultas con Y**

El siguiente fragmento de código te muestra cómo combinar consultas con Y.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Correos de un host específico, obtener todos los correos que llegaron antes de hoy y todos los correos que llegaron desde hace 7 días
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Combinando Consultas con O**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) proporciona el método [or()](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) que toma dos instancias de [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como parámetros. Obtiene los mensajes que coinciden con cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar mensajes que tienen “test” en el asunto o “noreply@host.com” como remitente. El siguiente fragmento de código te muestra cómo combinar consultas con O.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Especificar condición O
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

## **Filtración en InternalDate**

Los mensajes se pueden extraer del servidor en base a la InternalDate; sin embargo, a veces el servidor no devuelve todos los mensajes como se puede ver en la bandeja de entrada. Su razón puede ser la zona horaria del servidor, ya que puede no ser UTC para todos los servidores como [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envía comandos como 008 SEARCH ON 4-May-2014 de acuerdo con el [protocolo IMAP](https://datatracker.ietf.org/doc/html/rfc1730); sin embargo, el resultado puede diferir debido a la configuración de la zona horaria del servidor. Se ha añadido un nuevo miembro en [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) como [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) que ayuda además en la filtración de mensajes. El siguiente fragmento de código muestra el uso de [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) para filtrar mensajes.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e iniciar sesión en IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Establecer condiciones, Asunto contiene "Newsletter", Correos que llegaron hoy
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Construir la consulta y obtener la lista de mensajes
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Fecha Interna: " + info.getInternalDate());
}

// Desconectar de IMAP
client.dispose();
~~~

### **Filtrado de Correos con Sensibilidad a Mayúsculas y Minúsculas**

El siguiente fragmento de código te muestra cómo usar el filtrado de correos con sensibilidad a mayúsculas y minúsculas.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer condiciones, Asunto contiene "Newsletter", Correos que llegaron hoy
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~

### **Especificar Codificación para el Constructor de Consultas**

El constructor de [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) de la API se puede usar para especificar la codificación para la cadena de búsqueda. Esto también se puede establecer utilizando la [propiedad DefaultEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#getDefaultEncoding--) del MailQueryBuilder. El siguiente fragmento de código te muestra cómo especificar la codificación para el constructor de consultas.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer condiciones
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~

### **Filtrar Mensajes con Soporte de Paginación**

El [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona la capacidad de buscar mensajes del buzón y listarlos con soporte de paginación. El siguiente fragmento de código te muestra cómo filtrar mensajes con soporte de paginación.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// Este ejemplo muestra cómo buscar mensajes utilizando ImapClient de la API con soporte de paginación
/// Introducido en Aspose.Email para .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Agregar algunos mensajes de prueba
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), "111111111111111");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }
        String body = "2222222222222";
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), body);
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        client.selectFolder("Inbox");
        ImapQueryBuilder iqb = new ImapQueryBuilder();
        iqb.getBody().contains(body);
        MailQuery query = iqb.getQuery();

        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages(query);
        System.out.println(totalMessageInfoCol.size());

        //////////////////////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();

        PageSettings ps = new PageSettings();
        ps.setFolderName(ImapFolderInfo.IN_BOX);
        PageInfo pi = new PageInfo(itemsPerPage);
        ImapPageInfo pageInfo = client.listMessagesByPage(query, pi, ps);

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(query, pageInfo.getNextPage(), ps);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // conversión de foreach a while
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Filtrar Mensajes con Marca Personalizada**

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~

## **Filtrar Mensajes usando Búsqueda Personalizada**

Por ejemplo, el estándar RFC 3501 no permite buscar mensajes basados en la existencia de archivos adjuntos en los mensajes. Pero **Gmail** proporciona [Extensiones IMAP](https://developers.google.com/gmail/imap/imap-extensions) que permiten realizar dicha búsqueda. Aspose.Email proporciona el método [customSearch](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/#customSearch-java.lang.String-) de la clase [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) para realizar una consulta correspondiente.

El ejemplo de código a continuación muestra cómo recuperar una lista de mensajes de correo electrónico del servidor que tienen archivos adjuntos, utilizando el protocolo IMAP y un criterio de búsqueda personalizado:

```java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.customSearch("X-GM-RAW \"has:attachment\"");
MailQuery query = builder.getQuery();
messageInfoCol = client.listMessages(query);
```