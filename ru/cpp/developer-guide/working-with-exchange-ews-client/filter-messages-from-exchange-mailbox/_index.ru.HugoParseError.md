---
title: Фильтрация сообщений из почтового ящика Exchange
type: docs
weight: 30
url: /cpp/filter-messages-from-exchange-mailbox/
---

{{% alert color="primary" %}} 

Aspose.Email предоставляет возможность фильтровать сообщения из почтового ящика Exchange с помощью [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) и ExchangeQueryBuilder. Сообщения можно фильтровать по различным критериям, таким как дата, домен, messageId и уведомления о доставке почты. В этой статье показано, как фильтровать сообщения с сервера Exchange, используя различные критерии.

{{% /alert %}} 
Класс [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) предоставляет метод [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e), который получает все сообщения из почтового ящика. Чтобы получить только те сообщения, которые соответствуют некоторому условию, используйте перегруженный метод [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52), который принимает класс *MailQuery* в качестве аргумента. Класс *MailQuery* предоставляет различные свойства для указания условий, например, дата, тема, отправитель и получатель.
##  **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр *MailQuery* и установите желаемые свойства.
1. Вызовите метод [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) и передайте *MailQuery* в параметры, чтобы получить только отфильтрованные сообщения.

Следующий кодовый фрагмент показывает, как получить сообщения, у которых в теме есть строка "Newsletter" и которые были отправлены сегодня.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Фильтрация сообщений по критериям**
В приведенных выше примерах кода сообщения фильтруются на основе темы электронной почты и даты. Мы также можем фильтровать и по другим свойствам. Ниже приведены некоторые примеры установки условий с использованием *MailQuery*.
###  **Критерии фильтрации по сегодняшней дате**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе сегодняшней даты.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Критерии фильтрации диапазона дат**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе диапазона дат.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Критерии фильтрации по конкретному отправителю**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе конкретного отправителя.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Критерии фильтрации по конкретному домену**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе конкретного домена.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Критерии фильтрации по конкретному получателю**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе конкретного получателя.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Критерии фильтрации по MessageID**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе MessageID.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Критерии фильтрации всех уведомлений о доставке почты**
Следующий кодовый фрагмент показывает, как фильтровать электронные письма на основе всех уведомлений о доставке почты.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Фильтрация по размеру сообщения**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Построение сложных запросов**
Если разные свойства [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) установлены в отдельном выражении, все условия будут выполнены. Например, чтобы получить сообщение в определенном диапазоне дат и от конкретного хоста, напишите три выражения:
###  **Комбинирование запросов с AND**
Следующий кодовый фрагмент показывает, как комбинировать запросы с AND.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Комбинирование запросов с OR**

[MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) предоставляет метод [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4), который принимает два экземпляра *MailQuery* в качестве параметров. Он получает сообщения, которые соответствуют любому из двух указанных условий. В следующем примере фильтруются сообщения, которые имеют слово “test” в теме или “noreply@host.com” в качестве отправителя. Следующий кодовый фрагмент показывает, как комбинировать запросы с OR.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Фильтрация электронной почты с учетом регистра**
Электронные письма можно фильтровать с учетом регистра, указав флаг IgnoreCase в условиях фильтрации, как показано в следующем кодовом фрагменте.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Фильтрация сообщений с поддержкой разделения на страницы**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}