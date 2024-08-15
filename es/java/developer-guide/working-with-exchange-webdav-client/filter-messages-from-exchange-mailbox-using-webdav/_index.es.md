---
title: "Filtrar mensajes del buzón de Exchange mediante WebDAV"
url: /es/java/filter-messages-from-exchange-mailbox-using-webdav/
weight: 40
type: docs
---

{{% alert color="primary" %}}

The [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) La clase proporciona el método listMessages () que obtiene todos los mensajes de un buzón. Para obtener solo los mensajes que cumplen alguna condición, usa el método listMessages () sobrecargado, que toma el [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) clase como argumento. El [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) La clase proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros que distinguen mayúsculas y minúsculas para recuperar correos electrónicos del buzón.

{{% /alert %}}
## **Filtrar mensajes con Web Dav**
Para obtener los mensajes filtrados de un buzón:

1. Conéctese al servidor Exchange.
1. Crea una instancia de MailQuery y establece las propiedades deseadas.
1. Llame al método ExchangeClient.listMessages (consulta MailQuery) y pase la MailQuery a los parámetros para obtener solo los mensajes filtrados.

Los ejemplos de código que aparecen a continuación muestran cómo conectarse a un buzón de correo de Exchange y recibir mensajes con la cadena «Boletín» en el asunto y que se enviaron hoy.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// Subject contains "Newsletter"
builder.getSubject().contains("Newsletter");

// Emails that arrived today
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Build the query
MailQuery query = builder.getQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " message(s) found.");
~~~
## **Reciba mensajes que cumplan con criterios específicos**
Los ejemplos de código anteriores filtran los mensajes según el asunto y la fecha del correo electrónico. También podemos filtrar por otras propiedades. A continuación se muestran algunos ejemplos de cómo configurar las condiciones utilizando [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Filtrar criterios Fecha de hoy**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la fecha actual.


~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Rango de fechas de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del intervalo de fechas.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Remitente específico de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Dominio específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Destinatario específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Filtrar criterios por MessageID**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de MessageID.


~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Criterios de filtrado Todas las notificaciones de entrega de correo**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.


~~~Java
// Get Mail Delivery Notifications
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Creación de consultas complejas**
Si se establecen diferentes propiedades de QueryBuilder en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para recibir un mensaje de un determinado intervalo de fechas y de un anfitrión específico, escribe tres instrucciones:
#### **Combinación de consultas con AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// Emails from specific host
builder.getFrom().contains("SpecificHost.com");
// AND all emails that arrived before today
builder.getInternalDate().before(new Date());
// AND all emails that arrived since 7 days ago
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Combinación de consultas con OR**

`QueryBuilder` proporciona la `or()` método que requiere dos `MailQuery` instancias como parámetros. Recibe mensajes que cumplen cualquiera de las dos condiciones especificadas. El ejemplo siguiente filtra los mensajes que tienen la palabra «test» en el asunto o \"noreply@host.com\" como remitente.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Filtrado de correo electrónico sensible a mayúsculas**
Los correos electrónicos se pueden filtrar en función de la distinción entre mayúsculas y minúsculas especificando el indicador IgnoreCase en los criterios de filtro, como se muestra en el siguiente ejemplo.


~~~Java
//IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~
