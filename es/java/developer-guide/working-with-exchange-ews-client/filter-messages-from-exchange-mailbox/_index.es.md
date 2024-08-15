---
title: "Filtrar mensajes del buzón de Exchange"
url: /es/java/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Aspose.Email para Java ofrece la capacidad de filtrar los mensajes del buzón de Exchange mediante el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) and [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Los mensajes se pueden filtrar según diferentes criterios, como por fecha, dominio, identificador de mensaje y notificaciones de entrega de correo. En este artículo se muestra cómo filtrar los mensajes de Exchange Server utilizando diferentes criterios.

{{% /alert %}}
## **Filtrado de mensajes mediante EWS**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) la clase proporciona la [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)) método que toma el [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) clase como argumento. El [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) La clase proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros que distinguen mayúsculas y minúsculas para recuperar correos electrónicos del buzón.
### **Filtrado de mensajes**
Para obtener los mensajes filtrados de un buzón:

1. Conéctese al servidor Exchange.
1. Crea una instancia de MailQuery y establece las propiedades deseadas.
1. Llama al método iewsClient.listMessages () y pasa MailQuery a los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que tengan la cadena «Boletín» en el asunto y que se hayan enviado hoy.

~~~Java
try {
    // Connect to EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Query building by means of ExchangeQueryBuilder class
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Set Subject and Emails that arrived today
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Get list of messages
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " message(s) found.");

    // Disconnect from EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
### **Filtrar mensajes por criterios**
Los ejemplos de código anteriores filtran los mensajes según el asunto y la fecha del correo electrónico. También podemos filtrar por otras propiedades. A continuación se muestran algunos ejemplos de cómo configurar las condiciones utilizando [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Filtrar mensajes por fecha de hoy**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la fecha actual.

~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Filtrar mensajes por rango de fechas**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del intervalo de fechas.



~~~Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Filtrar mensajes por remitente específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.

~~~Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Filtrar mensajes por dominio específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.

~~~Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Filtrar mensajes por destinatario específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.

~~~Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Filtrar mensajes por MessageID**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de MessageID.

~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~
#### **Filtrar mensajes por todas las notificaciones de entrega de correo**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.

~~~Java
// Get Mail Delivery Notifications
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
#### **Filtrar mensajes por tamaño**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~
#### **Filtrar mensajes por valor de cadena**

El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la cadena especificada en los encabezados (asunto, de, a, cc). El [getText()](https://reference.aspose.com/email/java/com.aspose.email/exchangequerybuilder/#getText--) el método devuelve el valor de la cadena junto con el cuerpo del mensaje.

```java
 ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

builder.getText().equals("SomeText");

MailQuery query = builder.getQuery();

ExchangeMessageInfoCollection messages = ewsClient.listMessages("InboxUri", query, false);
```
#### **Filtrar mensajes en orden ascendente/descendente**

Aspose.Email proporciona la [ComparisonField.orderBy (booleano ascendente)](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) método que establece el valor que indica que el cliente utiliza la clasificación ascendente o descendente en el campo de búsqueda. Le permite ordenar los mensajes de correo electrónico en orden ascendente/descendente según los criterios especificados por [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/).

El siguiente fragmento de código muestra cómo filtrar los mensajes en orden ascendente/descendente:

```java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Report");
builder.getInternalDate().since(sinceDate);
builder.getSubject().orderBy(true); // sort the subject ascending
builder.getInternalDate().orderBy(false); // sort the date descending  

ExchangeMessageInfoCollection miColl = client.listMessages(client.getMailboxInfo().getInboxUri(), builder.getQuery());
```
### **Creación de consultas complejas**
Si es diferente [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) las propiedades se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para recibir un mensaje en un intervalo de fechas determinado y de un anfitrión específico, escribe tres afirmaciones:
#### **Combinación de consultas con AND**
El siguiente fragmento de código muestra cómo combinar consultas con AND.

~~~Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Combinación de consultas con OR**

[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) proporciona la [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) método que requiere dos [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) instancias como parámetros. Recibe mensajes que cumplen cualquiera de las dos condiciones especificadas. El ejemplo siguiente filtra los mensajes que tienen la palabra «test» en el asunto o \"noreply@host.com\" como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
### **Filtrado de correo electrónico sensible a mayúsculas**
Los correos electrónicos se pueden filtrar en función de la distinción entre mayúsculas y minúsculas especificando el indicador IgnoreCase en los criterios de filtro, como se muestra en el siguiente fragmento de código.

~~~Java
// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~
## **Filtrado de mensajes con soporte de paginación**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Query 1";
String str2 = sGuid + " - " + "Query 2";

MailQueryBuilder queryBuilder1 = new MailQueryBuilder();
queryBuilder1.getSubject().contains(str1);
MailQuery query1 = queryBuilder1.getQuery();
List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage);
pages.add(pageInfo);
int str1Count = pageInfo.getItems().size();
while (!pageInfo.getLastPage()) {
    pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage, pageInfo.getPageOffset() + 1);
    pages.add(pageInfo);
    str1Count += pageInfo.getItems().size();
}
~~~
