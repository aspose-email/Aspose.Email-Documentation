---
title: "Filtrar mensajes con AQS desde el buzón de Exchange"
url: /es/net/filter-messages-with-aqs-from-exchange-mailbox/
weight: 35
type: docs
---

[Sintaxis de consulta avanzada (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) es la sintaxis de consulta que usa Exchange como alternativa a los filtros de búsqueda para expresar los criterios de búsqueda. AQS es una forma más flexible de realizar búsquedas y ofrecer resultados de búsqueda para todos los campos de uso común en los elementos. AQS también es fácil de usar, de entender y de dominar rápidamente. El uso de AQS es adecuado para buscar mensajes por archivos adjuntos y destinatarios.

## Crear una consulta de búsqueda con AQS

Puede crear una consulta de búsqueda con AQS de la siguiente manera:

- [`ExchangeAdvancedSyntaxQueryBuilder`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que representa el generador de expresiones de búsqueda basadas en la sintaxis de consulta avanzada (AQS). O
- [`ExchangeAdvancedSyntaxMailQuery`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que crea una cadena AQS directamente basada en las palabras clave admitidas.

## Crear una consulta de búsqueda mediante el generador de consultas

Para crear una consulta de búsqueda con [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) necesitas:

- crear una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- crear una instancia de [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) y defina las propiedades necesarias para crear una consulta.

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) método y pase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instancia, devuelta por [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/) método, como uno de sus parámetros.

El ejemplo de código que aparece a continuación muestra cómo se pueden realizar los pasos anteriores:

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

## Cree una consulta de búsqueda directamente mediante AQS:

Para crear una consulta de búsqueda con [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) necesitas:

- crear una instancia de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- crear una instancia de [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) y pase una cadena de AQS. Consulte el [descripción de la sintaxis](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) método y pase [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) instancia como uno de sus parámetros.

El ejemplo de código que aparece a continuación muestra cómo se pueden realizar los pasos anteriores:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(product AND report)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```
