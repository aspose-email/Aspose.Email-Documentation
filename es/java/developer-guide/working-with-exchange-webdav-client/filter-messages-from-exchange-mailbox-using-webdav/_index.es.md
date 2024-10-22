---
title: "Filtrar mensajes de la bandeja de entrada de Exchange usando WebDav"
url: /es/java/filter-messages-from-exchange-mailbox-using-webdav/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

La clase [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) proporciona el método listMessages() que obtiene todos los mensajes de una bandeja de entrada. Para obtener solo los mensajes que coinciden con alguna condición, utilice el método sobrecargado listMessages() que toma la clase [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) como argumento. La clase [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros de sensibilidad a mayúsculas y minúsculas para recuperar correos electrónicos de la bandeja de entrada.

{{% /alert %}} 
## **Filtrar mensajes usando Web Dav**
Para obtener mensajes filtrados de una bandeja de entrada:

1. Conéctese al servidor de Exchange.
1. Cree una instancia de MailQuery y establezca las propiedades deseadas.
1. Llame al método ExchangeClient.listMessages(MailQuery query) y pase el MailQuery como parámetros para obtener solo los mensajes filtrados.

Los ejemplos de código a continuación muestran cómo conectarse a una bandeja de entrada de Exchange y obtener mensajes que tienen la cadena "Newsletter" en el asunto y fueron enviados hoy.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Construcción de la consulta mediante la clase ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// El asunto contiene "Newsletter"
builder.getSubject().contains("Newsletter");

// Correos electrónicos que llegaron hoy
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Construir la consulta
MailQuery query = builder.getQuery();

// Obtener lista de mensajes
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " mensaje(s) encontrado(s).");
~~~
## **Obtener mensajes que cumplan criterios específicos**
Los ejemplos de código anteriores filtran mensajes en función del asunto del correo electrónico y la fecha. También podemos filtrar por otras propiedades. A continuación se muestran algunos ejemplos de cómo establecer las condiciones utilizando [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Criterios de filtrado Fecha de hoy**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función de la fecha de hoy.


~~~Java
// Correos electrónicos que llegaron hoy
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Criterios de filtrado Rango de fechas**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función del rango de fechas.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Criterios de filtrado Remitente específico**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obtener correos electrónicos de un remitente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Criterios de filtrado Dominio específico**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obtener correos electrónicos de un dominio específico
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Criterios de filtrado Destinatario específico**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obtener correos electrónicos enviados a un destinatario específico
builder.getTo().contains("recipient");
~~~
#### **Criterios de filtrado por MessageID**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función del MessageID.


~~~Java
// Obtener correo electrónico con un MessageId específico
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Criterios de filtrado Todas las notificaciones de entrega de correo**
El siguiente fragmento de código le muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.


~~~Java
// Obtener notificaciones de entrega de correo
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Construcción de consultas complejas**
Si se establecen diferentes propiedades de QueryBuilder en declaraciones separadas, se cumplen todas las condiciones. Por ejemplo, para obtener un mensaje en un rango de fechas particular y de un host específico, escriba tres declaraciones:
#### **Combinación de consultas con AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// Correos electrónicos de un host específico
builder.getFrom().contains("SpecificHost.com");
// Y todos los correos electrónicos que llegaron antes de hoy
builder.getInternalDate().before(new Date());
// Y todos los correos electrónicos que llegaron desde hace 7 días
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Combinación de consultas con OR**

`QueryBuilder` proporciona el método `or()` que toma dos instancias de `MailQuery` como parámetros. Obtiene mensajes que coinciden con cualquiera de las dos condiciones especificadas. El ejemplo a continuación filtra mensajes que tienen la palabra "test" en el asunto o "noreply@host.com" como remitente.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Especificar condición OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Filtrado de correos electrónicos sensible a mayúsculas y minúsculas**
Los correos electrónicos se pueden filtrar en función de la sensibilidad a mayúsculas y minúsculas especificando la opción IgnoreCase en los criterios de filtro como se muestra en el siguiente ejemplo.


~~~Java
// IgnoreCase es verdadero
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~