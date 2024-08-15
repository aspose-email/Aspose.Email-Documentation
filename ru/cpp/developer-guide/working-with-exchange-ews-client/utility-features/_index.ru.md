---
title: "Функции утилиты"
url: /ru/cpp/utility-features/
weight: 120
type: docs
---

## **Отправка сообщения с опцией голосования**
Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Это делается путем включения таких вариантов голосования, как «Да», «Нет», «Возможно» и т. д. *FollowUpOptions* класс, предлагаемый Aspose.Email, предоставляет *VotingButtons* свойство, которое можно использовать для установки или получения значения опций голосования. В этой статье представлен подробный пример создания *MapiMessage* с возможностью голосования для создания опроса и последующей отправки сообщения с помощью клиента Exchange Web Service (EWS).
### **Создание и отправка сообщения с опциями голосования**
В следующем фрагменте кода показано, как создать новое сообщение, а затем отправить его с опциями голосования.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}


В следующем фрагменте кода показано определение *CreateTestMessage* метод, использованный в приведенном выше примере.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Игнорировать или обходить недействительный или просроченный сертификат SSL**
Aspose.Email может обрабатывать SSL-сертификаты на сервере Exchange, используя [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс. Если срок действия сертификата SSL истек или он стал недействительным, Aspose.Email выдает исключение из-за недействительного сертификата SSL. Избегайте таких ошибок SSL-сертификата, игнорируя их, используя метод, описанный в приведенном ниже коде. Зарегистрируйте обработчик обратного вызова в методе main () или init () и добавьте следующий метод в качестве члена класса.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Создание сообщений RE и FW из файлов MSG**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) позволяет разработчикам создавать сообщения RE (ответить/ответить всем) и FW (переслать) из исходного сообщения. Исходное сообщение идентифицируется путем выбора определенного [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) получено [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e). Другой аргумент является фактическим [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) для отправки в виде сообщения RE или FW. В следующем фрагменте кода показано, как отправить сообщение, а затем ответить на это сообщение и переслать это сообщение. Чтобы выполнить эту задачу, выполните следующие действия:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) возразите, предоставив действительные учетные данные.
1. Отправьте несколько образцов сообщений.
1. Позвоните [Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099), [ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41) and [Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27) методы отправки сообщений.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Добавление заголовков в запросы EWS**
API Aspose.Email позволяет добавлять заголовки в запросы Exchange. Это можно использовать для добавления заголовков в запросы EWS для разных заголовков, которые можно использовать для разных целей. Одним из таких примеров может быть добавление заголовка X-AnchorMailbox, который используется для решения проблем регулирования на сервере Exchange. [AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f) метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) используется для добавления заголовков к запросам EWS, как показано в следующем фрагменте кода.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Работа с единой системой обмена сообщениями**
Aspose.Email может получать информацию единой системы обмена сообщениями из Exchange Server 2010. В настоящее время поддерживается единая система обмена сообщениями, такая как получение сведений о конфигурации, инициирование исходящего вызова, получение информации о телефонном звонке по идентификатору вызова и отключение телефонного звонка по идентификатору. В следующем примере кода показано, как получить сведения о конфигурации единой системы обмена сообщениями из Microsoft Exchange Server 2010.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Советы по получению почты**
Сервер Microsoft Exchange добавил несколько новых функций в Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать советы по электронной почте при составлении сообщения электронной почты. Эти советы очень полезны, поскольку они предоставляют информацию до отправки электронного письма. Например, если адрес электронной почты указан неправильно в списке получателей, отображается подсказка, сообщающая вам, что адрес электронной почты недействителен. Кроме того, с помощью подсказок по почте вы можете просмотреть ответы, которые вы не получили в офисе, перед отправкой электронного письма: Exchange Server (2010 и 2013) отправляет подсказку по почте при составлении письма, если один или несколько получателей ответили, отсутствующие на рабочем месте. Для всех функций, описанных в этой статье, требуется пакет обновления 1 (SP1) для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как использовать [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс, использующий веб-службы Exchange, доступные в Microsoft Exchange Server 2007 и более поздних версиях.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}
