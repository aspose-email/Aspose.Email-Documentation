---
title: Утилитарные функции
type: docs
weight: 120
url: /net/utility-features/
---


## **Отправка сообщения с вариантом голосования**

Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Это делается путем включения вариантов голосования, таких как Да, Нет, Может быть и т.д. Класс FollowUpOptions, предлагаемый Aspose.Email, предоставляет свойство VotingButtons, которое может быть использовано для установки или получения значения вариантов голосования. Эта статья предоставляет детальный пример создания MapiMessage с вариантами голосования для создания опроса, а затем отправки сообщения с использованием клиента Exchange Web Service (EWS).

### **Создание и отправка сообщения с вариантами голосования**

Следующий кодовый фрагмент показывает, как создать новое сообщение, а затем отправить его с вариантами голосования.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Пример методов, используемых в примерах**

Следующий кодовый фрагмент показывает, как использовать методы, использованные в приведенном выше примере.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}

## **Игнорирование или обход недействительных или просроченных SSL сертификатов**

Aspose.Email может обрабатывать SSL сертификаты на Exchange Server, используя как [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/), так и [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) классы. Если SSL сертификат истек или стал недействительным, Aspose.Email генерирует исключение из-за недействительного SSL сертификата. Избегайте таких ошибок SSL сертификатов, игнорируя их с помощью метода, используемого в коде ниже. Зарегистрируйте обработчик обратного вызова в вашем методе main() или init() и добавьте метод ниже как член класса.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-IgnoringInvalidSSLCertificates-IgnoringInvalidSSLCertificates.cs" >}}

## **Создание сообщений RE и FW из файлов MSG**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) позволяет разработчикам создавать сообщения RE (Ответ/Ответить всем) и FW (Переслать) из исходного сообщения. Исходное сообщение определяется выбором определенного [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) из [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/), полученного с помощью [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). Другим аргументом является фактическое [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), которое будет отправлено в качестве сообщения RE или FW. Следующий кодовый фрагмент показывает, как создать образец учетной записи, который используется для отправки сообщения, а затем демонстрируются функции ответа и пересылки на этом образце сообщения. Для выполнения этой задачи:

1. Инициализируйте объект [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) с действительными учетными данными.
1. Отправьте несколько образцовых сообщений.
1. Вызовите функции [IEWSClient.Reply()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/reply/), [IEWSClient.ReplyAll()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/replyall/) и [IEWSClient.Forward()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/forward/) для отправки сообщений.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-CreateREAndFWMessages-CreateREAndFWMessages.cs" >}}

## **Поддержка отслеживания электронной почты**

API Aspose.Email предоставляет поддержку отслеживания электронной почты с использованием Уведомления о распределении сообщения (MDN). Это достигается путем запроса квитанций о прочтении и создания необходимой информации. Свойство [MailMessage.ReadReceiptTo](https://reference.aspose.com/email/net/aspose.email/mailmessage/readreceiptto/) получает или устанавливает адрес для квитанций о прочтении. Методы [CreateReadReceipt](https://reference.aspose.com/email/net/aspose.email/mailmessage/createreadreceipt/) и [ReadReceiptRequested](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/readreceiptrequested/) используются для создания и получения информации о том, запрашиваются ли квитанции о прочтении. Следующий кодовый фрагмент показывает, как отслеживать электронную почту с использованием API Aspose.Email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange-EmailTracking-EmailTracking.cs" >}}

## **Поддержка ведения журнала в клиентах Exchange**

API Aspose.Email предоставляет возможность предоставлять средства ведения журнала для клиента Exchange Web Service. Это можно достичь, настроив файл App.config.

### **Ведение журнала для EWS клиента**

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "LoggingForEWSClient.xml" >}}

## **Добавление заголовков в EWS запросы**

API Aspose.Email позволяет добавлять заголовки в запросы Exchange. Это можно использовать для добавления заголовков в запросы EWS для различных заголовков, которые могут использоваться для разных целей. Одним из таких примеров может быть добавление заголовка X-AnchorMailbox, который используется для управления проблемами с ограничением на сервере Exchange. Метод [AddHeader](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/addheader/) класса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) используется для добавления заголовков в запросы EWS, как показано в следующем кодовом фрагменте.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddingHeadersToEWSRequests-AddingHeadersToEWSRequests.cs" >}}

## **Работа с унифицированным сообщением**

Aspose.Email может извлекать информацию о унифицированном сообщении из Exchange Server 2010. Поддерживается унифицированное сообщение, такое как получение конфигурационной информации, инициирование исходящего вызова, получение информации о телефонном звонке по идентификатору вызова и отключение телефонного звонка по идентификатору. Следующий образец кода показывает, как извлечь информацию о конфигурации унифицированного сообщения из Microsoft Exchange Server 2010.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingUnifiedMessagingConfigurationInformation-GettingUnifiedMessagingConfigurationInformation.cs" >}}

## **Получение советов по электронной почте**

Microsoft Exchange Server добавил несколько новых функций с Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать советы по электронной почте при составлении сообщения электронной почты. Эти советы очень полезны, поскольку они предоставляют информацию перед отправкой электронной почты. Например, если адрес электронной почты неверен в списке получателей, отображается совет, чтобы сообщить вам, что адрес электронной почты недействителен. Советы по электронной почте также позволяют вам видеть автоматические ответы "вне офиса" перед отправкой электронной почты: Exchange Server (2010 и 2013) отправляет совет по электронной почте, когда сообщение составляется, если один или несколько получателей настроили автоматические ответы "вне офиса". Для всех функций, продемонстрированных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий кодовый фрагмент показывает, как использовать класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), который использует Exchange Web Services, доступные в Microsoft Exchange Server 2007 и более поздних версиях.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GetMailTips-GetMailTips.cs" >}}

## **Имитация Exchange**

Имитация Exchange позволяет кому-то выдавать себя за другую учетную запись и выполнять задачи и операции, используя разрешения учетной записи, за которую он выдает себя, вместо своих собственных. В то время как делегирование позволяет пользователям действовать от имени других пользователей, имитация позволяет им действовать как другие пользователи. Aspose.Email поддерживает имитацию Exchange. Класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) предоставляет методы [ImpersonateUser](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/impersonateuser/) и [ResetImpersonation](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/resetimpersonation/) для облегчения этой функции.

Для выполнения этой задачи:

1. Инициализируйте ExchangeWebServiceClient для пользователя 1.
1. Инициализируйте ExchangeWebServiceClient для пользователя 2.
1. Добавьте тестовые сообщения к учетным записям.
1. Включите имитацию.
1. Сбросьте имитацию.

Следующий кодовый фрагмент показывает, как использовать класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) для реализации функции имитации.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ExchangeImpersonationUsingEWS-ExchangeImpersonationUsingEWS.cs" >}}

## **Функция автопоиск с использованием EWS**

API Aspose.Email позволяет вам узнать настройки Exchange Server с помощью клиента EWS. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AutoDiscoverUsingEWS-AutoDiscoverUsingEWS.cs" >}}

## **Прерывание операции восстановления PST на сервер Exchange**

API Aspose.Email позволяет вам восстановить файл PST на сервер Exchange. Однако, если операция занимает много времени из-за большого размера файла PST, может потребоваться указать критерий для прерывания операции. Это можно реализовать с помощью API, как показано в следующем образце кода.

**Примечание:** В примере необходимо также добавить следующий класс.

``` cs

 public class CustomAbortRestoreException : Exception { }

```

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AbortPSTToExchangeServerOperation-AbortPSTToExchangeServerOperation.cs" >}}