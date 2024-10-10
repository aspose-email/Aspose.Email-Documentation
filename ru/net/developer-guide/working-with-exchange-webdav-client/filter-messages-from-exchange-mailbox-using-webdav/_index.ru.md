---
title: "Фильтрация сообщений из почтового ящика Exchange с использованием WebDav"
url: /ru/net/filter-messages-from-exchange-mailbox-using-webdav/
weight: 30
type: docs
---


## **Фильтрация сообщений с использованием WebDav**
Класс [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) предоставляет метод [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие некоторым условиям, используйте перегруженный метод [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2), который принимает класс [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) в качестве аргумента. Класс [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) предоставляет различные свойства для указания условий, например, дата, тема, отправитель и получатель. Кроме того, API также позволяет применять фильтры с учетом регистра для извлечения электронных писем из почтового ящика.
### **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) и установите необходимые свойства.
1. Вызовите метод [ExchangeClient.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) и передайте [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) в параметрах, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к IMAP почтовому ящику и получить сообщения, которые содержат строку "Newsletter" в теме и были отправлены сегодня.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesFromExchangeMailbox-FilterMessagesFromExchangeMailbox.cs" >}}
### **Фильтрация сообщений по критериям**
Примеры кода выше фильтруют сообщения на основе темы электронной почты и даты. Мы также можем фильтровать по другим свойствам. Ниже приведены примеры настройки условий с использованием [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Фильтрация по критерию сегодняшней даты**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе сегодняшней даты.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsWithTodayDate.cs" >}}
#### **Фильтрация по критерию диапазона дат**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе диапазона дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsOverDateRange.cs" >}}
#### **Фильтрация по критерию конкретного отправителя**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе конкретного отправителя.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificSenderEmails.cs" >}}
#### **Фильтрация по критерию конкретного домена**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе конкретного домена.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificDomainEmails.cs" >}}
#### **Фильтрация по критерию конкретного получателя**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе конкретного получателя.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificRecipientEmails.cs" >}}
#### **Фильтрация по критерию по MessageID**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе MessageID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificMessageIdEmail.cs" >}}
#### **Фильтрация по критерию всех уведомлений о доставке почты**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основе всех уведомлений о доставке почты.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetMailDeliveryNotifications.cs" >}}
### **Создание сложных запросов**
Если разные свойства [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) установлены в отдельном операторе, все условия совпадают. Например, чтобы получить сообщение в определенном диапазоне дат и от конкретного хоста, напишите три оператора:
#### **Объединение запросов с AND**
Следующий фрагмент кода показывает, как объединить запросы с помощью AND.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с OR**

[ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) предоставляет метод [Or()](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or), который принимает два экземпляра [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery)в качестве параметров. Он получает сообщения, которые соответствуют любому из двух указанных условий. Пример ниже фильтрует сообщения, которые содержат слово “test” в теме или “noreply@host.com” в качестве отправителя. Следующий фрагмент кода показывает, как объединить запросы с помощью OR.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombiningQueriesWithOR.cs" >}}
### **Фильтрация электронной почты с учетом регистра**
Электронные письма можно фильтровать с учетом регистра, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-CaseSensitiveEmailsFilteringUsingExchangeClient-CaseSensitiveEmailsFilteringUsingExchangeClient.cs" >}}