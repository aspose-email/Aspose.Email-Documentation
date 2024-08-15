---
title: "Функции утилиты"
url: /ru/net/utility-features/
weight: 120
type: docs
---


## **Отправка сообщения с опцией голосования**

Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Для этого можно включить такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Класс FollowupOptions, предлагаемый Aspose.Email, предоставляет свойство VotingButtons, которое можно использовать для установки или получения значений параметров голосования. В этой статье приведен подробный пример создания MapiMessage с опциями голосования для создания опроса и последующей отправки сообщения с помощью клиента Exchange Web Service (EWS).

### **Создание и отправка сообщения с опциями голосования**

В следующем фрагменте кода показано, как создать новое сообщение, а затем отправить его с опциями голосования.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Примерные методы, используемые в примерах**

В следующем фрагменте кода показано, как использовать методы, использованные в приведенном выше примере.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}

## **Игнорировать или обходить недействительный или просроченный сертификат SSL**

Aspose.Email может обрабатывать SSL-сертификаты на сервере Exchange, используя оба [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) and [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) классы. Если срок действия сертификата SSL истек или он стал недействительным, Aspose.Email выдает исключение из-за недействительного сертификата SSL. Избегайте таких ошибок SSL-сертификата, игнорируя их, используя метод, описанный в приведенном ниже коде. Зарегистрируйте обработчик обратного вызова в методе main () или init () и добавьте следующий метод в качестве члена класса.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}

## **Создание сообщений RE и FW из файлов MSG**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) позволяет разработчикам создавать сообщения RE (ответить/ответить всем) и FW (переслать) из исходного сообщения. Исходное сообщение идентифицируется путем выбора определенного [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) from [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) получено [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). Другой аргумент является фактическим [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для отправки в виде сообщения RE или FW. В следующем фрагменте кода показано, как создать образец учетной записи, которая будет использоваться для отправки сообщения, а затем на примере этого примера сообщения продемонстрированы функции «Ответить» и «Переслать». Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) возразите, предоставив действительные учетные данные.
1. Отправьте несколько образцов сообщений.
1. Позвоните [IEWSClient.Reply()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/reply/), [IEWSClient.ReplyAll()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/replyall/) and [IEWSClient.Forward()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/forward/) функции для отправки сообщений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}

## **Поддержка отслеживания электронной почты**

Aspose.Email API обеспечивает поддержку отслеживания электронной почты с помощью уведомления об удалении сообщений (MDN). Это достигается путем запроса квитанций о прочтении и создания необходимой информации. [MailMessage.ReadReceiptTo](https://reference.aspose.com/email/net/aspose.email/mailmessage/readreceiptto/) свойство получает или задает заданный адрес квитанции о прочтении. [CreateReadReceipt](https://reference.aspose.com/email/net/aspose.email/mailmessage/createreadreceipt/) and [ReadReceiptRequested](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/readreceiptrequested/) методы используются для создания и получения информации о том, запрашиваются ли квитанции о прочтении. В следующем фрагменте кода показано, как отслеживать сообщения по электронной почте с помощью Aspose.Email API.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}

## **Поддержка входа в систему клиентов Exchange**

API Aspose.Email предоставляет возможность предоставлять возможность ведения журнала клиента веб-службы Exchange. Это можно сделать, настроив файл App.config.

### **Ведение журнала для клиента EWS**

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}

## **Добавление заголовков в запросы EWS**

API Aspose.Email позволяет добавлять заголовки в запросы Exchange. Это можно использовать для добавления заголовков в запросы EWS для разных заголовков, которые можно использовать для разных целей. Одним из таких примеров может служить добавление заголовка X-AnchorMailbox, который используется для решения проблем регулирования на сервере Exchange. [AddHeader](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/addheader/) метод [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) используется для добавления заголовков к запросам EWS, как показано в следующем фрагменте кода.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}

## **Работа с единой системой обмена сообщениями**

Aspose.Email может получать информацию единой системы обмена сообщениями из Exchange Server 2010. В настоящее время поддерживается единая система обмена сообщениями, такая как получение сведений о конфигурации, инициирование исходящего вызова, получение информации о телефонном звонке по идентификатору вызова и отключение телефонного звонка по идентификатору. В следующем примере кода показано, как получить сведения о конфигурации единой системы обмена сообщениями из Microsoft Exchange Server 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Советы по получению почты**

Сервер Microsoft Exchange добавил несколько новых функций в Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать советы по электронной почте при составлении сообщения электронной почты. Эти советы очень полезны, поскольку они предоставляют информацию до отправки электронного письма. Например, если адрес электронной почты указан неправильно в списке получателей, отображается подсказка, сообщающая вам, что адрес электронной почты недействителен. Кроме того, с помощью подсказок по почте вы можете просмотреть ответы, полученные от сотрудников, прежде чем отправлять электронное письмо: Exchange Server (2010 и 2013) отправляет сообщение по почте при составлении письма, если один или несколько получателей ответили, отсутствующие на рабочем месте. Для всех функций, описанных в этой статье, требуется пакет обновления 1 (SP1) для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как использовать [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс, использующий веб-службы Exchange, доступные в Microsoft Exchange Server 2007 и более поздних версиях.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Выдача себя за биржу**

Выдача себя за другое лицо Exchange позволяет пользователю выдавать себя за другую учетную запись и выполнять задачи и операции, используя разрешения выдаваемой учетной записи вместо своих собственных. Если делегирование позволяет пользователям действовать от имени других пользователей, то выдача себя за другое лицо позволяет им действовать как другие пользователи. Aspose.Email поддерживает выдачу себя за другое лицо в Exchange. [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс предоставляет [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) and [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) методы, облегчающие эту функцию.

Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте клиент ExchangeWebServiceClient для пользователя 1.
1. Инициализируйте клиент ExchangeWebServiceClient для пользователя 2.
1. Добавляйте тестовые сообщения к учетным записям.
1. Включите выдачу себя за другое лицо.
1. Сбросить олицетворение.

В следующем фрагменте кода показано, как использовать [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс для реализации функции Impersonation.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}

## **Функция автоматического обнаружения с помощью EWS**

API Aspose.Email позволяет узнать о настройках сервера Exchange с помощью клиента EWS. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}

## **Прервать операцию восстановления PST на сервере Exchange**

API Aspose.Email позволяет восстановить файл PST на сервере Exchange. Однако если операция занимает много времени из-за большого размера файла PST, возможно, потребуется указать критерий для прерывания операции. Это можно сделать с помощью API, как показано в следующем примере кода.

**Note:** В пример также необходимо добавить следующий класс.

``` cs

 public class CustomAbortRestoreException : Exception { }

```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}
