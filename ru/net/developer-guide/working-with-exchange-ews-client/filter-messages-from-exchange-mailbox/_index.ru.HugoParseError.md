---
title: Фильтрация сообщений из почтового ящика Exchange
type: docs
weight: 30
url: /net/filter-messages-from-exchange-mailbox/
---


{{% alert color="primary" %}}

Aspose.Email для .NET предоставляет возможность фильтровать сообщения из почтового ящика Exchange, используя EWSClient и ExchangeQueryBuilder. Сообщения могут фильтроваться по различным критериям, таким как дата, домен, идентификатор сообщения и по уведомлениям о доставке почты. В этой статье показано, как фильтровать сообщения с сервера Exchange, используя различные критерии.

{{% /alert %}} 

## **Фильтрация сообщений с использованием EWS**

Интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) предоставляет метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие некоторым условиям, используйте перегруженный метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages), принимающий класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве аргумента. Класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) предоставляет различные свойства для указания условий, например, дата, тема, отправитель и получатель. Кроме того, API также позволяет применять фильтры по учету регистра для извлечения писем из почтового ящика.

### **Фильтрация сообщений по критериям**

Чтобы получить отфильтрованные сообщения из почтового ящика:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и установите желаемые свойства.
1. Вызовите метод [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) и передайте [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в параметрах, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к IMAP почтовому ящику и получить сообщения, в которых в теме присутствует строка "Newsletter" и отправлены сегодня.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **Фильтрация сообщений по сегодняшней дате**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании сегодняшней даты.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **Фильтрация сообщений по диапазону дат**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании диапазона дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **Фильтрация сообщений по конкретному отправителю**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **Фильтрация сообщений по конкретному домену**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного домена.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **Фильтрация сообщений по конкретному получателю**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного получателя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **Фильтрация сообщений по ID сообщения**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании ID сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **Фильтрация сообщений по всем уведомлениям о доставке почты**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании всех уведомлений о доставке почты.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **Фильтрация сообщений по размеру сообщения**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}


### **Построение сложных запросов**

Если различные свойства [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) установлены в отдельном выражении, все условия совпадают. Например, чтобы получить сообщение в определённом диапазоне дат и от конкретного хоста, напишите три выражения:

#### **Объединение запросов с помощью AND**

Следующий фрагмент кода показывает, как объединить запросы с помощью AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с помощью OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) предоставляет метод [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or), который принимает два экземпляра [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В примере ниже фильтруются сообщения, которые содержат слово “test” в теме или “noreply@host.com” в качестве отправителя. Следующий фрагмент кода показывает, как объединить запросы с помощью OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

### **Фильтрация электронной почты с учетом регистра**

Электронные письма могут фильтроваться с учетом регистра, используя флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

## **Фильтрация сообщений с поддержкой постраничного просмотра**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

## **Сортировка отфильтрованных сообщений по возрастанию/убыванию**

Фильтрация электронной почты может поддерживаться с сортировкой сообщений по возрастанию/убыванию. В этом случае используется метод [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/), чтобы указать порядок, в котором результаты поиска электронной почты сортируются с помощью класса MailQueryBuilder. Этот метод позволяет определить критерии сортировки для поискового запроса, указывая, должны ли результаты сортироваться по возрастанию или убыванию на основе конкретного свойства.

Метод принимает параметр ascending, который указывает порядок сортировки для указанного свойства. Если параметр ascending равен true, это означает, что результаты поиска должны быть отсортированы по возрастанию. Напротив, если параметр ascending равен false, это означает, что результаты поиска должны быть отсортированы по убыванию.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // сортировать по возрастанию темы
builder.InternalDate.OrderBy(false); // сортировать по убыванию даты

MailQuery query = builder.GetQuery();

// Получить список сообщений
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

В приведённом выше фрагменте кода метод OrderBy применяется дважды, один раз для темы и один раз для даты электронной почты. В результате выполнения метода ListMessages с переданным запросом мы получим список сообщений с темой, содержащей слово "Report", которые были получены в указанную дату или позже. В то же время результаты будут отсортированы по теме в порядке возрастания. Это означает, что сообщения будут отсортированы в алфавитном порядке от A до Z в зависимости от их темы. Также результаты будут отсортированы по дате в порядке убывания. Это означает, что сообщения будут упорядочены от самых новых к самым старым.
