---
title: "Filtrar mensajes del servidor mediante el cliente IMAP"
url: /es/java/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---


The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) la clase proporciona la [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) método que toma [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) como argumento. El [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) La clase proporciona varias propiedades para especificar las condiciones, por ejemplo, fecha, asunto, remitente, destinatario, etc. El primer ejemplo ilustra cómo filtrar los mensajes en función de la fecha y el asunto. También mostramos cómo filtrar según otros criterios y cómo crear consultas más complejas. La API también ofrece la capacidad de aplicar criterios de búsqueda que distinguen mayúsculas y minúsculas para que coincidan con los criterios de filtrado exactos. La API también permite especificar la codificación de la cadena de búsqueda para filtrar los mensajes del buzón.

## **Filtrar mensajes del buzón**

1. [Conectarse e iniciar sesión en un servidor IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Crea una instancia del [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) y establecer las propiedades
1. Llame al [IMAPClient.ListMessages (consulta de MailQuery)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages-com.aspose.email.MailQuery-) método y pase el [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) con los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que llegaron hoy y que tienen la palabra «boletín» en el asunto.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " message(s) found.");
// Disconnect from IMAP
client.dispose();
~~~

## **Reciba mensajes que cumplan con criterios específicos**

[Los ejemplos de código anteriores](#filtering-messages-from-mailbox) filtra los mensajes según el asunto y la fecha del correo electrónico. También podemos usar otras propiedades para establecer otras condiciones compatibles. A continuación se muestran algunos ejemplos de cómo configurar las condiciones mediante [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Los siguientes fragmentos de código muestran cómo filtrar los correos electrónicos según:

1. La fecha de hoy.
1. Un intervalo de fechas.
1. De un remitente específico.
1. De un dominio específico.
1. De un destinatario específico.

### **Fecha de hoy**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en Fecha de hoy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~
### **Date Range*
The following code snippet shows you how to filter emails on the date range.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Remitente específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos de un remitente específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

### **Dominio específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos en un dominio específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~

### **Destinatario específico**

El siguiente fragmento de código muestra cómo filtrar los correos electrónicos de un destinatario específico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~

## **Creación de consultas complejas**

Si es diferente [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) las propiedades se establecen en declaraciones separadas, entonces todas las condiciones coincidirían. Por ejemplo, si queremos recibir mensajes entre un intervalo de fechas y los de un anfitrión específico, necesitamos escribir tres declaraciones.

### **Combinación de consultas con AND**

El siguiente fragmento de código muestra cómo combinar consultas con AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Combinación de consultas con OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) proporciona la [or()](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) método que requiere dos [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) instancias como parámetros. Obtiene los mensajes que cumplen cualquiera de las dos condiciones especificadas. El siguiente fragmento de código muestra cómo filtrar los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

## **Filtración en InternalDate**

Los mensajes se pueden extraer del servidor en función de InternalDate; sin embargo, a veces el servidor no devuelve todos los mensajes tal como aparecen en la bandeja de entrada. Su motivo puede ser la zona horaria del servidor, ya que es posible que no sea UTC para todos los servidores, como [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envía comandos como 008 SEARCH EL 4 de mayo de 2014 según el [Protocolo IMAP](https://datatracker.ietf.org/doc/html/rfc1730) sin embargo, el resultado puede variar debido a la configuración de la zona horaria del servidor. Se agrega un nuevo miembro en [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) as [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) lo que ayuda aún más a filtrar los mensajes. El siguiente fragmento de código muestra el uso de [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) para filtrar los mensajes.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Internal Date: " + info.getInternalDate());
}

// Disconnect from IMAP
client.dispose();
~~~

### **Filtrado de correos electrónicos sensibles a mayúsculas**

El siguiente fragmento de código muestra cómo usar el filtrado de correos electrónicos que distingue mayúsculas y minúsculas.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~

### **Especificar la codificación para Query Builder**

Las API [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) el constructor se puede usar para especificar la codificación de la cadena de búsqueda. Esto también se puede configurar usando el [DefaultEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#getDefaultEncoding--) propiedad de MailQueryBuilder. El siguiente fragmento de código muestra cómo especificar la codificación del generador de consultas.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~

### **Filtrar mensajes con soporte de paginación**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) brinda la capacidad de buscar mensajes en el buzón y enumerarlos con soporte de paginación. El siguiente fragmento de código muestra cómo filtrar los mensajes que admiten la paginación.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// This example shows how to search for messages using ImapClient of the API with paging support
/// Introduced in Aspose.Email for .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Append some test messages
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
        // foreach to while statements conversion
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

## **Filtrar mensajes con bandera personalizada**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~

## **Filtrar mensajes mediante la búsqueda personalizada**

Por ejemplo, el estándar RFC 3501 no permite una búsqueda de mensajes basada en la existencia de archivos adjuntos en los mensajes. Pero **Gmail** provides [Extensiones IMAP](https://developers.google.com/gmail/imap/imap-extensions) que permiten realizar dicha búsqueda. Aspose.Email proporciona la [customSearch](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/#customSearch-java.lang.String-) método del [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) clase para realizar la consulta correspondiente.

El ejemplo de código que aparece a continuación muestra cómo recuperar una lista de mensajes de correo electrónico del servidor que tienen archivos adjuntos, mediante el protocolo IMAP y un criterio de búsqueda personalizado:

```java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.customSearch("X-GM-RAW \"has:attachment\"");
MailQuery query = builder.getQuery();
messageInfoCol = client.listMessages(query);
```
