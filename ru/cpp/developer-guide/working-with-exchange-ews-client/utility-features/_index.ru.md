---
title: "Утилитарные функции"
url: /ru/cpp/utility-features/
weight: 120
type: docs
---

## **Отправка сообщения с вариантом голосования**
Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Это делается включением вариантов голосования, таких как Да, Нет, Может быть и т.д. Класс *FollowUpOptions*, предлагаемый Aspose.Email, предоставляет свойство *VotingButtons*, которое можно использовать для установки или получения значения вариантов голосования. Эта статья предоставляет подробный пример создания *MapiMessage* с вариантами голосования для создания опроса, а затем отправки сообщения с использованием клиента Exchange Web Service (EWS).
### **Создание и отправка сообщения с вариантами голосования**
Следующий фрагмент кода показывает, как создать новое сообщение и отправить его с вариантами голосования.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cpp" >}}

Следующий фрагмент кода показывает определение метода *CreateTestMessage*, используемого в приведенном выше примере.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cpp" >}}
## **Игнорирование или обход недействительного или просроченного SSL сертификата**
Aspose.Email может обрабатывать SSL сертификаты на Exchange Server с использованием класса [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Если SSL сертификат просрочен или стал недействительным, Aspose.Email выбрасывает исключение из-за недействительного SSL сертификата. Избегайте таких ошибок SSL сертификатов, игнорируя их с помощью метода, используемого в приведенном ниже коде. Зарегистрируйте обработчик обратного вызова в вашем методе main() или init() и добавьте метод ниже как член класса.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cpp" >}}
## **Создание сообщений RE и FW из MSG файлов**
[IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) позволяет разработчикам создавать сообщения RE (Ответ/Ответить всем) и FW (Переслать) из исходного сообщения. Исходное сообщение определяется выбором конкретного [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) из [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection), полученной с помощью [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e). Другим аргументом является фактическое [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message), которое будет отправлено как сообщение RE или FW. Следующий фрагмент кода показывает, как отправить сообщение, затем ответить на это сообщение и переслать это сообщение. Чтобы выполнить эту задачу:

1. Инициализируйте объект [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), предоставив действительные учетные данные.
1. Отправьте несколько тестовых сообщений.
1. Вызовите методы [Reply()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2d925824adc83ffdebeb7d135bd99099), [ReplyAll()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac08b12a3db4f1e20eaaa0d5f99c27c41) и [Forward()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1040eb913667b6702b0253e48a48ec27) для отправки сообщений.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cpp" >}}
## **Добавление заголовков в EWS запросы**
Aspose.Email API позволяет добавлять заголовки к запросам Exchange. Это может быть использовано для добавления заголовков к EWS запросам для различных целей. Одним из таких примеров может быть добавление заголовка X-AnchorMailbox, который используется для управления проблемами с ограничением на сервере Exchange. Метод [AddHeader](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a93b0dd8364564686a15e720d8e5a4e9f) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) используется для добавления заголовков к запросам EWS, как показано в следующем фрагменте кода.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cpp" >}}
## **Работа с унифицированным сообщением**
Aspose.Email может извлекать информацию об унифицированном сообщении из Exchange Server 2010. Поддерживается унифицированное сообщение, такое как получение информации о конфигурации, инициирование исходящего звонка, извлечение информации о телефонном звонке по идентификатору вызова и отключение телефонного звонка по идентификатору. Следующий пример кода показывает, как извлечь информацию о конфигурации унифицированного сообщения из Microsoft Exchange Server 2010.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cpp" >}}
## **Получение советов по почте**
Microsoft Exchange Server добавил несколько новых функций с Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать советы по почте при составлении электронного сообщения. Эти советы очень полезны, так как они предоставляют информацию перед отправкой электронной почты. Например, если адрес электронной почты неверен в списке получателей, отображается совет, чтобы уведомить вас о том, что адрес электронной почты недействителен. Советы по почте также позволяют увидеть автоматические ответы "вне офиса" перед отправкой электронной почты: Exchange Server (2010 и 2013) отправляет совет по почте, когда электронное письмо составляется, если один или несколько получателей установили автоматические ответы "вне офиса". Для всех функций, продемонстрированных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий фрагмент кода показывает, как использовать класс [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client), который использует Exchange Web Services, доступные в Microsoft Exchange Server 2007 и более поздних версиях.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailTips-GetMailTips.cpp" >}}