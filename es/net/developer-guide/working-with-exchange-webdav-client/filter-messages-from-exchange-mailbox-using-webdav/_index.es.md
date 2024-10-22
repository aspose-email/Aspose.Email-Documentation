---
title: "Filtrar mensajes de la bandeja de entrada de Exchange usando WebDav"
url: /es/net/filter-messages-from-exchange-mailbox-using-webdav/
weight: 30
type: docs
---

## **Filtrando mensajes usando WebDav**
La clase [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) proporciona el método [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) que obtiene todos los mensajes de una bandeja de entrada. Para obtener solo los mensajes que coincidan con alguna condición, utiliza el método sobrecargado [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) que toma la clase [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) como argumento. La clase [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) proporciona varias propiedades para especificar condiciones, por ejemplo, fecha, asunto, remitente y destinatario. Además, la API también permite aplicar filtros de sensibilidad a mayúsculas y minúsculas para recuperar correos electrónicos de la bandeja de entrada.
### **Filtrando mensajes**
Para obtener mensajes filtrados de una bandeja de entrada:

1. Conéctate al servidor de Exchange.
1. Crea una instancia de [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) y configura las propiedades deseadas.
1. Llama al método [ExchangeClient.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) y pasa el [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) en los parámetros para obtener solo los mensajes filtrados.

El siguiente fragmento de código te muestra cómo conectarte a una bandeja de entrada IMAP y obtener mensajes que contienen la cadena "Newsletter" en el asunto y fueron enviados hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesFromExchangeMailbox-FilterMessagesFromExchangeMailbox.cs" >}}
### **Filtrar mensajes por criterio**
Los ejemplos de código anteriores filtran mensajes en función del asunto del correo electrónico y la fecha. También podemos filtrar por otras propiedades. A continuación se presentan algunos ejemplos de establecimiento de condiciones utilizando [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Criterio de filtrado Fecha de hoy**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de la fecha de hoy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsWithTodayDate.cs" >}}
#### **Criterio de filtrado Rango de fechas**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función del rango de fechas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsOverDateRange.cs" >}}
#### **Criterio de filtrado Remitente específico**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de un remitente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificSenderEmails.cs" >}}
#### **Criterio de filtrado Dominio específico**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de un dominio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificDomainEmails.cs" >}}
#### **Criterio de filtrado Destinatario específico**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de un destinatario específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificRecipientEmails.cs" >}}
#### **Criterio de filtrado Por MessageID**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificMessageIdEmail.cs" >}}
#### **Criterio de filtrado Todas las notificaciones de entrega de correo**
El siguiente fragmento de código te muestra cómo filtrar todos los correos electrónicos en función de todas las notificaciones de entrega de correo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetMailDeliveryNotifications.cs" >}}
### **Construyendo consultas complejas**
Si diferentes propiedades de [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) se establecen en una declaración separada, se cumplen todas las condiciones. Por ejemplo, para obtener un mensaje en un rango de fechas particular y de un host específico, escribe tres declaraciones:
#### **Combinando consultas con AND**
El siguiente fragmento de código te muestra cómo combinar consultas con AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombineQueriesWithAND.cs" >}}

#### **Combinando consultas con OR**

[ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) proporciona el método [Or()](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or) que toma dos instancias de [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) como parámetros. Obtiene mensajes que coinciden con cualquiera de las dos condiciones especificadas. El ejemplo a continuación filtra mensajes que tienen la palabra “test” en el asunto o “noreply@host.com” como remitente. El siguiente fragmento de código te muestra cómo combinar consultas con OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombiningQueriesWithOR.cs" >}}
### **Filtrado de correos electrónicos con sensibilidad a mayúsculas y minúsculas**
Los correos electrónicos se pueden filtrar en función de la sensibilidad a mayúsculas y minúsculas especificando la bandera IgnoreCase en los criterios de filtrado, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-CaseSensitiveEmailsFilteringUsingExchangeClient-CaseSensitiveEmailsFilteringUsingExchangeClient.cs" >}}