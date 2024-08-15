---
title: "Фильтрация сообщений из почтового ящика Exchange с помощью AQS"
url: /ru/net/filter-messages-with-aqs-from-exchange-mailbox/
weight: 35
type: docs
---

[Расширенный синтаксис запросов (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) это синтаксис запроса, используемый Exchange в качестве альтернативы фильтрам поиска для выражения критериев поиска. AQS — это более гибкий способ поиска и выдачи результатов поиска по всем часто используемым полям элементов. AQS также удобен в использовании, прост в понимании и быстро осваивается. Использование AQS подходит для поиска сообщений по вложениям и получателям.

## Создание поискового запроса с помощью AQS

Вы можете создать поисковый запрос с помощью AQS следующим образом:

- [`ExchangeAdvancedSyntaxQueryBuilder`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), который представляет собой конструктор поисковых выражений на основе расширенного синтаксиса запросов (AQS). Или
- [`ExchangeAdvancedSyntaxMailQuery`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), который создает строку AQS непосредственно на основе поддерживаемых ключевых слов.

## Создайте поисковый запрос с помощью конструктора запросов

Чтобы создать поисковый запрос с помощью [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) вам необходимо:

- создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- создайте экземпляр [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) и задайте необходимые свойства для построения запроса.

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) метод и пропуск [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) экземпляр, возвращенный [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/) метод, как один из его параметров.

В приведенном ниже примере кода показано, как можно выполнить указанные выше шаги:

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

## Создайте поисковый запрос напрямую с помощью AQS:

Чтобы создать поисковый запрос с помощью [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) вам необходимо:

- создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) using [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/) method

- создайте экземпляр [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) и передайте строку AQS. См. [описание синтаксиса](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) or [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) метод и пропуск [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) экземпляр в качестве одного из его параметров.

В приведенном ниже примере кода показано, как можно выполнить указанные выше шаги:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(product AND report)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```
