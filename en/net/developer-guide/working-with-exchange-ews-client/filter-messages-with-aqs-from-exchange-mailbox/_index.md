---
title: Filter Messages With AQS From Exchange Mailbox
type: docs
weight: 35
url: /net/filter-messages-with-aqs-from-exchange-mailbox/
---

[Advanced Query Syntax (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) is the query syntax used by Exchange as an alternative to searching filters for expressing search criteria. AQS is a more flexible way to perform searches and deliver search results for all commonly used fields on the items. AQS is also user-friendly, easy to understand and quickly to master. Using AQS is suitable for finding messages by attachments and recipients.

## Creating a search query with AQS

You can create a search query with AQS by:

- [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), which represents the builder of search expression based on the Advanced Query Syntax (AQS).
  or
- [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), which creates an AQS string directly based on the supported keywords.

## Create a search query using query builder

To create a search query with [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) you need to:

- create an instance of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- create an instance of [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) and set necessary properties to build a query.

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) method and pass [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) instance, returned by [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/) method, as one of its parameters.

The code sample below shows how the above steps can be accomplished:

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

## Сreate a search query directly by using AQS:

To create a search query with [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) you need to :

- create an instance of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- create an instance of [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) and pass an AQS string. See the [syntax description](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) method and pass [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) instance as one of its parameters.

The code sample below shows how the above steps can be accomplished:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(product AND report)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```
