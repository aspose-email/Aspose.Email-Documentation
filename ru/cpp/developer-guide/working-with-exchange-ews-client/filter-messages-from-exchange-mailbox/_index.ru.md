---
title: "Фильтрация сообщений из почтового ящика Exchange"
url: /ru/cpp/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Aspose.Email предоставляет возможность фильтровать сообщения из почтового ящика Exchange с помощью [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) и конструктор запросов Exchange. Сообщения можно фильтровать по различным критериям, например по дате, домену, идентификатору сообщения и уведомлениям о доставке почты. В этой статье показано, как фильтровать сообщения с сервера Exchange по различным критериям.

{{% /alert %}}
The [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) класс предоставляет [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) метод, который принимает *MailQuery* класс в качестве аргумента. *MailQuery* класс предоставляет различные свойства для указания условий, например даты, темы, отправителя и получателя.
##  **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика, выполните следующие действия:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр *MailQuery* и задайте нужные свойства.
1. Позвоните [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) метод и передайте *MailQuery* в параметрах, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как получать сообщения со строкой «Newsletter» в теме и отправленные сегодня.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Фильтрация сообщений по критериям**
Приведенные выше примеры кода фильтруют сообщения по теме и дате письма. Мы также можем фильтровать другие свойства. Ниже приведены несколько примеров настройки условий с помощью *MailQuery*.
###  **Критерии фильтрации: сегодняшняя дата**
В следующем фрагменте кода показано, как фильтровать электронные письма на основе сегодняшней даты.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Диапазон дат критериев фильтрации**
В следующем фрагменте кода показано, как фильтровать электронные письма по диапазону дат.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Критерии фильтрации: конкретный отправитель**
В следующем фрагменте кода показано, как фильтровать электронные письма по определенному отправителю.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Критерии фильтрации: конкретный домен**
В следующем фрагменте кода показано, как фильтровать электронные письма на основе определенного домена.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Критерии фильтрации: конкретный получатель**
В следующем фрагменте кода показано, как фильтровать электронные письма на основе конкретного получателя.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Критерии фильтрации по MessageID**
В следующем фрагменте кода показано, как фильтровать электронные письма на основе MessageID.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Критерии фильтрации Все уведомления о доставке почты**
В следующем фрагменте кода показано, как фильтровать электронные письма на основе всех уведомлений о доставке почты.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Фильтровать по размеру сообщения**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Создание сложных запросов**
Если отличается [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) свойства задаются в отдельном выражении, все условия соблюдены. Например, чтобы получить сообщение в определенном диапазоне дат и от определенного хоста, напишите три выражения:
###  **Объединение запросов с AND**
В следующем фрагменте кода показано, как комбинировать запросы с AND.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Объединение запросов с OR**

[MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) обеспечивает [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4) метод, который требует двух *MailQuery* экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В приведенном ниже примере отфильтровываются сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Фильтрация электронной почты с учетом регистра**
Электронные письма можно отфильтровать на основе чувствительности к регистру, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Фильтрация сообщений с поддержкой пейджинга**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}
