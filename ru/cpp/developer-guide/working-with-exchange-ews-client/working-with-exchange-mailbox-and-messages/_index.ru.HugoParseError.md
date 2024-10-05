---
title: Работа с почтовым ящиком Exchange и сообщениями
type: docs
weight: 20
url: /cpp/working-with-exchange-mailbox-and-messages/
---

## **Получение информации о почтовом ящике с использованием EWS**
Вы можете получить информацию о почтовом ящике с сервера Exchange, вызвав метод [GetMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Получите информацию о почтовом ящике из свойств, таких как MailboxUri, InboxUri и DraftsUri. Эта статья показывает, как получить доступ к информации о почтовом ящике с использованием Exchange Web Services.

Для подключения к серверу Exchange с использованием Exchange Web Services (EWS) используйте класс [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Этот класс использует EWS для подключения и управления элементами на сервере Exchange. Следующий кодовый Snippet показывает, как получить информацию о почтовом ящике с использованием обменных веб-сервисов.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Отправка электронных сообщений**
Вы можете отправлять электронные сообщения с использованием сервера Exchange с помощью метода [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c), который принимает экземпляр [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) в качестве параметра и отправляет электронное письмо. Эта статья объясняет, как отправлять электронные сообщения с использованием Exchange Web Services.

Следующий кодовый Snippet показывает, как отправить электронные сообщения с использованием [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Чтение электронных писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, и некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получать доступ к почтовым ящикам других пользователей с помощью Aspose.Email. Этот API предоставляет механизм для доступа к папкам и электронным письмам из других почтовых ящиков с использованием класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Эта функциональность может быть достигнута с использованием перегруженного метода [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) и предоставлением адреса электронной почты пользователя в качестве параметра.

Следующий кодовый Snippet показывает, как читать электронные письма с использованием класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **Список сообщений**
Список электронных сообщений в почтовом ящике Exchange можно получить, вызвав метод [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca). Получите основную информацию о сообщениях, такую как тему, отправителя, получателя и идентификатор сообщения, используя метод [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca).
### **Простой список сообщений**
Чтобы перечислить сообщения в почтовом ящике Exchange:

1. Создайте экземпляр класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Вызовите метод [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca), чтобы получить коллекцию сообщений.
1. Пройдите через коллекцию и отображайте информацию о сообщениях.

Следующий кодовый Snippet показывает, как подключиться к серверу Exchange с использованием EWS и перечислить сообщения из папки «Входящие».



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **Перечисление сообщений из разных папок**
Вышеуказанный кодовый Snippet перечисляет все сообщения в папке «Входящие». Также возможно получить список сообщений из других папок. Метод [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) принимает URI папки в качестве параметра. При условии, что URI папки действителен, вы можете получить список сообщений из этой папки. Используйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->xxxFolderUri свойство, чтобы получить URI различных папок. Остальная часть кода такая же, как для получения списка сообщений. Следующий кодовый Snippet показывает, как перечислить сообщения из разных папок с использованием EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Перечисление сообщений с поддержкой постраничного вывода**
Следующий кодонов Snippet показывает, как получить список сообщений с поддержкой постраничного вывода.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Получение информации о типах сообщений из ExchangeMessageInfo**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}
## **Сохранение сообщений**
Эта статья показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их на диск в форматах EML и MSG:

- Сохранить в формате EML на диске.
- Сохранить в потоке памяти.
- Сохранить в формате MSG.
### **Сохранение сообщений в формате EML**
Чтобы получить сообщения и сохранить в формате EML:

1. Создайте экземпляр класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Укажите mailboxUri, имя пользователя, пароль и домен.
1. Вызовите метод [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca), чтобы получить экземпляр коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Пройдите через коллекцию [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection), чтобы получить уникальный URI для каждого сообщения.
1. Вызовите метод [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) и передайте уникальный URI и место сохранения в качестве параметров.

Следующий кодовый Snippet показывает, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}
### **Сохранение сообщений в поток памяти**
Вместо того, чтобы сохранять файлы EML на диск, их можно сохранить в поток памяти. Это полезно, когда вы хотите сохранить поток в каком-то месте хранения, например, в базе данных. После того как поток был сохранен в базе данных, вы можете перезагрузить файл EML в классе [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). Следующий кодовый Snippet показывает, как сохранить сообщения из почтового ящика сервера Exchange в поток памяти с использованием EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}
### **Сохранение сообщений в формате MSG**
Метод [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите метод [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905), который возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). Затем вызовите метод [MailMessage->Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c), чтобы сохранить сообщение в MSG. Следующий кодовый Snippet показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их в формате MSG с использованием EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}
## **Получение ExchangeMessageInfo из URI сообщения**
Электронное сообщение представляется своим уникальным идентификатором, URI, и является неотъемлемой частью объекта ExchangeMessageInfo. В случае, если доступен только URI сообщения, объект [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) также можно получить с помощью этой доступной информации. Перегруженная версия метода [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) принимает список идентификаторов и возвращает коллекцию [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). Следующий кодовый Snippet показывает, как получить [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) из URI сообщения.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}
## **Получение сообщений из почтового ящика сервера Exchange**
Метод [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) используется для получения списка сообщений из почтового ящика сервера Exchange. Метод [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) получает основную информацию о сообщениях, например, тему, идентификатор сообщения, отправителя и получателя. Чтобы получить полные данные о сообщении, Aspose.Email предоставляет метод [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message). Класс [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) затем предоставляет детали сообщения, такие как текст, заголовки и вложения. Чтобы получить сообщения из почтового ящика сервера Exchange:

1. Создайте экземпляр типа [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Вызовите метод [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca), чтобы получить [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Пройдите через коллекцию [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection), чтобы получить значения [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7).
1. Вызовите [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) и передайте [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) в качестве параметра.

Следующий кодовый Snippet демонстрирует получение всех сообщений с использованием EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}
## **Предварительное получение размера сообщения**
Microsoft Outlook InterOp предоставляет возможность извлечения размера сообщения перед фактическим получением полного сообщения с сервера. В случае API Aspose.Email сводная информация, полученная с обменного сервера, представлена классом [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info). Он предоставляет возможность получения размера сообщения с помощью свойства [Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a). Для получения размера сообщения стандартный вызов [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) используется для извлечения [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). Следующий кодовый Snippet показывает, как отобразить размер сообщения с использованием класса [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}
## **Загрузка сообщений из общих папок**
Microsoft Exchange Server позволяет пользователям создавать общие папки и размещать в них сообщения. Чтобы сделать это через ваше приложение, используйте класс Aspose.Email [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client), чтобы подключиться к серверу Exchange и читать и загружать сообщения и записи из общих папок. Следующий кодовый Snippet показывает, как читать все общие папки и подпапки, а также перечислять и загружать любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 и выше, поскольку только они поддерживают EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Перемещение сообщений**
Вы можете перемещать электронные сообщения из одной папки в другую с помощью метода [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) Move. Он принимает следующие параметры:

- Уникальный URI сообщения, которое необходимо переместить.
- Уникальный URI папки назначения.
### **Перемещение сообщений между папками**
Следующий кодовый Snippet показывает, как переместить сообщение в почтовом ящике из папки «Входящие» в папку под названием «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе определенных критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, которые соответствуют данному условию, в папку «Обработано».

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}
## **Удаление сообщений**
Вы можете удалить электронные сообщения из папки с помощью метода [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1). Он принимает уникальный URI сообщения в качестве параметра.

Следующий кодовый Snippet показывает, как удалить сообщение из папки «Входящие». В этом примере код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает сообщения на основе определенных критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удаляет сообщение.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}
## **Копирование сообщений**
API Aspose.Email позволяет копировать сообщение из одной папки в другую с помощью метода [IEWSClient->CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f). Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.
### **Копирование сообщения в другую папку**
Следующий кодовый Snippet показывает, как скопировать сообщение в другую папку.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}
