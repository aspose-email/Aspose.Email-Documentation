---
title: "Фильтрация сообщений с помощью AQS из почтового ящика Exchange"
url: /ru/net/filter-messages-with-aqs-from-exchange-mailbox/
weight: 35
type: docs
---

[Расширенный синтаксис запросов (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) — это синтаксис запросов, используемый Exchange в качестве альтернативы поисковым фильтрам для выражения критериев поиска. AQS является более гибким способом выполнения поисков и предоставления результатов поиска для всех общепринятых полей элементов. AQS также удобен для пользователя, легко воспринимается и быстро осваивается. Использование AQS подходит для поиска сообщений по вложениям и получателям.

## Создание запроса поиска с помощью AQS

Вы можете создать запрос поиска с помощью AQS следующим образом:

- [`ExchangeAdvancedSyntaxQueryBuilder`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), который представляет собой строитель поискового выражения, основанный на Расширенном синтаксисе запросов (AQS). Или
- [`ExchangeAdvancedSyntaxMailQuery`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), который создает строку AQS непосредственно на основе поддерживаемых ключевых слов.

## Создание запроса поиска с использованием конструктора запросов

Чтобы создать запрос поиска с помощью [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) вам необходимо:

- создать экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) с использованием метода [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/)

- создать экземпляр [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) и установить необходимые свойства для построения запроса.

- вызвать метод [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) или [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) и передать экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/), возвращаемый методом [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/), в качестве одного из его параметров.

Пример кода ниже показывает, как можно осуществить вышеперечисленные шаги:

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

## Создание запроса поиска непосредственно с использованием AQS:

Чтобы создать запрос поиска с помощью [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) вам необходимо:

- создать экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) с использованием метода [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/)

- создать экземпляр [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) и передать строку AQS. См. [описание синтаксиса](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- вызвать метод [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) или [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/) и передать экземпляр [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) в качестве одного из его параметров.

Пример кода ниже показывает, как можно осуществить вышеперечисленные шаги:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(product AND report)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```