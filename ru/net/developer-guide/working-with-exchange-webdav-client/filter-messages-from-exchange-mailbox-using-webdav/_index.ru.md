---
title: "Фильтрация сообщений из почтового ящика Exchange с помощью WebDAV"
url: /ru/net/filter-messages-from-exchange-mailbox-using-webdav/
weight: 30
type: docs
---


## **Фильтрация сообщений с помощью WebDAV**
The [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) класс предоставляет [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) метод, который принимает [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) класс в качестве аргумента. [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) класс предоставляет различные свойства для указания условий, например даты, темы, отправителя и получателя. Кроме того, API также позволяет применять фильтры, учитывающие регистр символов, для получения писем из почтового ящика.
### **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика, выполните следующие действия:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) и задайте нужные свойства.
1. Позвоните [ExchangeClient.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) метод и передайте [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) в параметрах, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения со строкой «Newsletter» в теме и отправленные сегодня.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesFromExchangeMailbox-FilterMessagesFromExchangeMailbox.cs" >}}
### **Фильтрация сообщений по критериям**
Приведенные выше примеры кода фильтруют сообщения по теме и дате письма. Мы также можем фильтровать другие свойства. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Критерии фильтрации: сегодняшняя дата**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе сегодняшней даты.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsWithTodayDate.cs" >}}
#### **Диапазон дат критериев фильтрации**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе диапазона дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsOverDateRange.cs" >}}
#### **Критерии фильтрации: конкретный отправитель**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного отправителя.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificSenderEmails.cs" >}}
#### **Критерии фильтрации: конкретный домен**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе определенного домена.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificDomainEmails.cs" >}}
#### **Критерии фильтрации: конкретный получатель**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного получателя.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificRecipientEmails.cs" >}}
#### **Критерии фильтрации по MessageID**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе MessageID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificMessageIdEmail.cs" >}}
#### **Критерии фильтрации Все уведомления о доставке почты**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе всех уведомлений о доставке почты.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetMailDeliveryNotifications.cs" >}}
### **Создание сложных запросов**
Если отличается [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) свойства задаются в отдельном выражении, все условия соблюдены. Например, чтобы получить сообщение в определенном диапазоне дат и от определенного хоста, напишите три выражения:
#### **Объединение запросов с AND**
В следующем фрагменте кода показано, как комбинировать запросы с AND.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с OR**

[ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) обеспечивает [Or()](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or) метод, который требует двух [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery)экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В приведенном ниже примере отфильтровываются сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombiningQueriesWithOR.cs" >}}
### **Фильтрация электронной почты с учетом регистра**
Электронные письма можно отфильтровать на основе чувствительности к регистру, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-CaseSensitiveEmailsFilteringUsingExchangeClient-CaseSensitiveEmailsFilteringUsingExchangeClient.cs" >}}
