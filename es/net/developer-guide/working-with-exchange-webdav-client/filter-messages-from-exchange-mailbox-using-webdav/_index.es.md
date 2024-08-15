---
title: "Filtrar mensajes del buzón de Exchange mediante WebDAV"
url: /es/net/filter-messages-from-exchange-mailbox-using-webdav/
weight: 30
type: docs
---


## **Filtrado de mensajes mediante WebDAV**
The [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) la clase proporciona la [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método que obtiene todos los mensajes de un buzón. Para recibir solo los mensajes que cumplen alguna condición, utilice el método sobrecargado [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) método que toma el [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) clase como argumento. El [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) La clase proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros que distingan mayúsculas y minúsculas para recuperar correos electrónicos del buzón.
### **Filtrado de mensajes**
Para obtener los mensajes filtrados de un buzón:

1. Conéctese al servidor Exchange.
1. Crea una instancia de [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) y defina las propiedades deseadas.
1. Llame al [ExchangeClient.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) método y pase el [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código muestra cómo conectarse a un buzón IMAP y recibir los mensajes que tengan la cadena «Boletín» en el asunto y que se hayan enviado hoy.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesFromExchangeMailbox-FilterMessagesFromExchangeMailbox.cs" >}}
### **Filtrar mensajes según criterios**
Los ejemplos de código anteriores filtran los mensajes según el asunto y la fecha del correo electrónico. También podemos filtrar por otras propiedades. A continuación se muestran algunos ejemplos de cómo configurar las condiciones utilizando [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Filtrar criterios Fecha de hoy**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de la fecha actual.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsWithTodayDate.cs" >}}
#### **Rango de fechas de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función del intervalo de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsOverDateRange.cs" >}}
#### **Remitente específico de criterios de filtro**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificSenderEmails.cs" >}}
#### **Dominio específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificDomainEmails.cs" >}}
#### **Destinatario específico de criterios de filtrado**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificRecipientEmails.cs" >}}
#### **Filtrar criterios por MessageID**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de MessageID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificMessageIdEmail.cs" >}}
#### **Criterios de filtrado Todas las notificaciones de entrega de correo**
El siguiente fragmento de código muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetMailDeliveryNotifications.cs" >}}
### **Creación de consultas complejas**
Si es diferente [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) las propiedades se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para recibir un mensaje en un intervalo de fechas determinado y de un anfitrión específico, escribe tres afirmaciones:
#### **Combinación de consultas con AND**
El siguiente fragmento de código muestra cómo combinar consultas con AND.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombineQueriesWithAND.cs" >}}

#### **Combinación de consultas con OR**

[ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) proporciona la [Or()](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or) método que requiere dos [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery)instancias como parámetros. Recibe mensajes que cumplen cualquiera de las dos condiciones especificadas. El ejemplo siguiente filtra los mensajes que tienen la palabra «test» en el asunto o «noreply@host.com» como remitente. En el siguiente fragmento de código, se muestra cómo combinar consultas con OR.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombiningQueriesWithOR.cs" >}}
### **Filtrado de correo electrónico sensible a mayúsculas**
Los correos electrónicos se pueden filtrar en función de la distinción entre mayúsculas y minúsculas especificando el indicador IgnoreCase en los criterios de filtro, como se muestra en el siguiente fragmento de código.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-CaseSensitiveEmailsFilteringUsingExchangeClient-CaseSensitiveEmailsFilteringUsingExchangeClient.cs" >}}
