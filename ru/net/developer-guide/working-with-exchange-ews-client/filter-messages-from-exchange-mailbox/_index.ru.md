---
title: "Фильтрация сообщений из почтового ящика Exchange"
url: /ru/net/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Aspose.Email for .NET предоставляет возможность фильтровать сообщения из почтового ящика Exchange с помощью EWSclient и ExchangeQueryBuilder. Сообщения можно фильтровать по различным критериям, таким как дата, домен, идентификатор сообщения и уведомления о доставке почты. В этой статье показано, как фильтровать сообщения с сервера Exchange по разным критериям.

{{% /alert %}}

## **Фильтрация сообщений с помощью EWS**

The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) интерфейс обеспечивает [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) метод, который принимает [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс в качестве аргумента. [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс предоставляет различные свойства для указания условий, например даты, темы, отправителя и получателя. Кроме того, API также позволяет применять фильтры, учитывающие регистр символов, для получения писем из почтового ящика.

### **Фильтрация сообщений по критериям**

Чтобы получить отфильтрованные сообщения из почтового ящика, выполните следующие действия:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и задайте нужные свойства.
1. Позвоните [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) метод и передайте [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в параметрах, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения со строкой «Newsletter» в теме и отправленные сегодня.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **Отфильтровать сообщения по сегодняшней дате**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе сегодняшней даты.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **Фильтрация сообщений по диапазону дат**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе диапазона дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **Фильтрация сообщений по определенному отправителю**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **Фильтрация сообщений по определенному домену**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе определенного домена.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **Фильтрация сообщений по определенному получателю**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного получателя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **Фильтровать сообщения по MessageID**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **Фильтрация сообщений по всем уведомлениям о доставке почты**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе всех уведомлений о доставке почты.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **Фильтрация сообщений по размеру сообщения**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}


### **Создание сложных запросов**

Если отличается [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) свойства задаются в отдельном выражении, все условия соблюдены. Например, чтобы получить сообщение в определенном диапазоне дат и от определенного хоста, напишите три выражения:

#### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) обеспечивает [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) метод, который требует двух [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В приведенном ниже примере отфильтровываются сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

### **Фильтрация электронной почты с учетом регистра**

Электронные письма можно отфильтровать на основе чувствительности к регистру, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

## **Фильтрация сообщений с поддержкой пейджинга**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

## **Сортировка отфильтрованных сообщений в порядке возрастания/убывания**

Фильтрация электронной почты может поддерживаться сортировкой сообщений в порядке возрастания/убывания. В этом случае [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/) метод используется для указания порядка сортировки результатов поиска по электронной почте с помощью класса MailQueryBuilder. Этот метод позволяет определить критерии сортировки поискового запроса, указав, следует ли сортировать результаты в порядке возрастания или убывания в зависимости от определенного свойства.

Метод принимает параметр по возрастанию, который определяет порядок сортировки указанного свойства. Если параметр по возрастанию имеет значение true, это означает, что результаты поиска должны быть отсортированы в порядке возрастания. И наоборот, если параметр по возрастанию равен false, это означает, что результаты поиска следует отсортировать в порядке убывания.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // sort the subject ascending
builder.InternalDate.OrderBy(false); // sort the date descending

MailQuery query = builder.GetQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

В приведенном выше фрагменте кода метод orderBy применяется дважды: один раз для темы и один раз для даты письма. В результате выполнения метода listMessages с переданным запросом мы получим список сообщений с темой, содержащей слово «Отчет», которые были получены в указанную дату или позже. При этом результаты будут отсортированы по темам в порядке возрастания. Это означает, что сообщения будут отсортированы в алфавитном порядке от А до Я в зависимости от их темы. Кроме того, результаты будут отсортированы по дате в порядке убывания. Это означает, что сообщения будут отсортированы от новых к самым старым.
