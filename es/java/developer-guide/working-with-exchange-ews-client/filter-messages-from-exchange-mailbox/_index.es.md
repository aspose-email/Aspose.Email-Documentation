---
title: "Filtrar Mensajes Desde el Buzón de Exchange"
url: /es/java/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email para Java proporciona la capacidad de filtrar mensajes desde un Buzón de Exchange utilizando el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) y [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Los mensajes pueden ser filtrados a través de diferentes criterios como por fecha, dominio, message-id, y por Notificaciones de Entrega de Correo. Este artículo muestra cómo filtrar mensajes desde un Servidor Exchange utilizando diferentes Criterios.

{{% /alert %}} 
## **Filtrando Mensajes Usando EWS**
La [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) clase proporciona el [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)) método que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que coinciden con alguna condición, utiliza el método sobrecargado [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)) que toma la clase [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) como argumento. La clase [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros de case-sensitivity para recuperar correos del buzón.
### **Filtrando Mensajes**
Para obtener mensajes filtrados de un buzón:

1. Conectar al servidor de Exchange.
1. Crear una instancia de MailQuery y configurar las propiedades deseadas.
1. Llamar al método IEWSClient.listMessages() y pasar el MailQuery en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y obtener mensajes que tienen la cadena "Newsletter" en el asunto y fueron enviados hoy.

~~~Java
try {
    // Conectar a EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Construcción de la consulta mediante la clase ExchangeQueryBuilder
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Establecer Asunto y Correos que llegaron hoy
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Obtener lista de mensajes
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " mensaje(s) encontrado(s).");

    // Desconectar de EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~ 
### **Filtrar Mensajes por Criterios**
Los ejemplos de código anteriores filtran mensajes basados en el asunto del correo y la fecha. También podemos filtrar otras propiedades. A continuación se presentan algunos ejemplos de cómo establecer las condiciones utilizando [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Filtrar Mensajes por la Fecha de Hoy**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de la fecha de hoy.

~~~Java
// Correos que llegaron hoy
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~ 
#### **Filtrar Mensajes por Rango de Fechas**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función del rango de fechas.

~~~Java
// Correos que llegaron en los últimos 7 días
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~ 
#### **Filtrar Mensajes por Remitente Específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de un remitente específico.

~~~Java
// Obtener correos de un remitente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~ 
#### **Filtrar Mensajes por Dominio Específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de un dominio específico.

~~~Java
// Obtener correos de un dominio específico
builder.getFrom().contains("SpecificHost.com");
~~~ 
#### **Filtrar Mensajes por Destinatario Específico**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de un destinatario específico.

~~~Java
// Obtener correos enviados a un destinatario específico
builder.getTo().contains("recipient");
~~~ 
#### **Filtrar Mensajes por MessageID**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de MessageID.

~~~Java
// Obtener correo con un MessageId específico
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~ 
#### **Filtrar Mensajes por Todas las Notificaciones de Entrega de Correo**
El siguiente fragmento de código muestra cómo filtrar todos los correos en función de todas las notificaciones de entrega de correo.

~~~Java
// Obtener Notificaciones de Entrega de Correo
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~ 
#### **Filtrar Mensajes por Tamaño**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~ 
#### **Filtrar Mensajes por Valor de Cadena**

El siguiente fragmento de código muestra cómo filtrar todos los correos en función de la cadena especificada en los encabezados (asunto, de, para, cc). El método [getText()](https://reference.aspose.com/email/java/com.aspose.email/exchangequerybuilder/#getText--) devuelve el valor de la cadena junto con el cuerpo del mensaje.

```java
 ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

builder.getText().equals("SomeText");

MailQuery query = builder.getQuery();

ExchangeMessageInfoCollection messages = ewsClient.listMessages("InboxUri", query, false);
```
#### **Filtrar Mensajes en Orden Ascendente/Descendente**

Aspose.Email proporciona el método [ComparisonField.orderBy(boolean ascending)](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) que establece el valor que indica que el cliente utiliza ordenación ascendente o descendente en el campo de búsqueda. Permite ordenar los mensajes de correo en orden ascendente/descendente basado en los criterios especificados por [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/).

El siguiente fragmento de código demuestra cómo filtrar mensajes en orden ascendente/descendente:

```java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Report");
builder.getInternalDate().since(sinceDate);
builder.getSubject().orderBy(true); // ordenar el asunto ascendente
builder.getInternalDate().orderBy(false); // ordenar la fecha descendente  

ExchangeMessageInfoCollection miColl = client.listMessages(client.getMailboxInfo().getInboxUri(), builder.getQuery());
```
### **Construyendo Consultas Complejas**
Si diferentes [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) propiedades se establecen en una declaración separada, todas las condiciones se coinciden. Por ejemplo, para obtener un mensaje en un rango de fechas particular y de un host específico, escribe tres declaraciones:
#### **Combinando Consultas con AND**
El siguiente fragmento de código muestra cómo combinar consultas con AND.

~~~Java
// Correos de un host específico, obtener todos los correos que llegaron antes de hoy y todos los correos que llegaron desde hace 7 días
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~ 
#### **Combinando Consultas con OR**

[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) proporciona el [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) método que toma dos [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) instancias como parámetros. Obtiene mensajes que coinciden con cualquiera de las dos condiciones especificadas. El ejemplo a continuación filtra mensajes que tienen la palabra "test" en el asunto o "noreply@host.com" como remitente. El siguiente fragmento de código muestra cómo combinar consultas con OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~ 
### **Filtrado de Correos con Sensibilidad a Mayúsculas y Minúsculas**
Los correos pueden ser filtrados en función de la sensibilidad a mayúsculas y minúsculas especificando la bandera IgnoreCase en los criterios de filtrado como se muestra en el siguiente fragmento de código.

~~~Java
// Construcción de la consulta mediante la clase ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~ 
## **Filtrando Mensajes con Soporte de Paginación**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Consulta 1";
String str2 = sGuid + " - " + "Consulta 2";

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