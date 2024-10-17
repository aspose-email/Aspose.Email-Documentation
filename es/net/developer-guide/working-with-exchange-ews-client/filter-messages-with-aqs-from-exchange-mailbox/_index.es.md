---
title: "Filtrar mensajes con AQS desde el buzón de Exchange"
url: /es/net/filter-messages-with-aqs-from-exchange-mailbox/
weight: 35
type: docs
---

[La Sintaxis de Consulta Avanzada (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) es la sintaxis de consulta utilizada por Exchange como una alternativa a los filtros de búsqueda para expresar criterios de búsqueda. AQS es una forma más flexible de realizar búsquedas y entregar resultados de búsqueda para todos los campos comúnmente utilizados en los elementos. AQS también es fácil de usar, fácil de entender y rápido de dominar. Utilizar AQS es adecuado para encontrar mensajes por adjuntos y destinatarios.

## Crear una consulta de búsqueda con AQS

Puede crear una consulta de búsqueda con AQS mediante:

- [`ExchangeAdvancedSyntaxQueryBuilder`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que representa el generador de expresiones de búsqueda basado en la Sintaxis de Consulta Avanzada (AQS). O
- [`ExchangeAdvancedSyntaxMailQuery`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que crea una cadena AQS directamente basada en las palabras clave admitidas.

## Crear una consulta de búsqueda utilizando el generador de consultas

Para crear una consulta de búsqueda con [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) necesita:

- crear una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) usando el método [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/)

- crear una instancia de [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) y establecer las propiedades necesarias para construir una consulta.

- llamar al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) o [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) y pasar la instancia [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) devuelta por el método [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/) como uno de sus parámetros.

El siguiente fragmento de código muestra cómo se pueden lograr los pasos anteriores:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    var advancedBuilder = new ExchangeAdvancedSyntaxQueryBuilder();
    advancedBuilder.From.Equals("Jim Martin");
    advancedBuilder.Subject.Contains("report");
    advancedBuilder.HasAttachment.Equals(true);

    var messages = client.ListMessages(client.MailboxInfo.InboxUri, advancedBuilder.GetQuery());
}
```

## Crear una consulta de búsqueda directamente utilizando AQS:

Para crear una consulta de búsqueda con [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) necesita:

- crear una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) usando el método [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/)

- crear una instancia de [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) y pasar una cadena AQS. Vea la [descripción de la sintaxis](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- llamar al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) o [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) y pasar la instancia [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) como uno de sus parámetros.

El siguiente fragmento de código muestra cómo se pueden lograr los pasos anteriores:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(product AND report)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```