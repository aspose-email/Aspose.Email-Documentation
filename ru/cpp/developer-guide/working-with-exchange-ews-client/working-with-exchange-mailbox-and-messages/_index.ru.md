---
title: "Работа с почтовым ящиком и сообщениями Exchange"
url: /ru/cpp/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
---

## **Получение данных почтового ящика с помощью EWS**
Сведения о почтовом ящике можно получить с сервера Exchange, позвонив в [GetMailboxInfo ](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927)метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс. Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Получите информацию о почтовом ящике из таких свойств, как MailboxURI, InboxURI и DraftSURI. В этой статье показано, как получить доступ к сведениям о почтовом ящике с помощью веб-служб Exchange.

Чтобы подключиться к серверу Exchange с помощью веб-служб Exchange (EWS), используйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс. В этом классе используется EWS для подключения к элементам на сервере Exchange и управления ими. В следующем фрагменте кода показано, как получить информацию о почтовом ящике с помощью веб-служб Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Отправка сообщений электронной почты**
Вы можете отправлять сообщения электронной почты с помощью сервера Exchange с [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) метод принимает [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) экземпляр в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять сообщения электронной почты с помощью веб-служб Exchange.

В следующем фрагменте кода показано, как отправлять сообщения электронной почты с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Чтение писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, а некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей с помощью Aspose.Email. Этот API предоставляет механизм доступа к папкам и электронным письмам из других почтовых ящиков с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс. Эта функциональность может быть достигнута с помощью перегруженных [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) метод и указание адреса электронной почты пользователя в качестве параметра.

В следующем фрагменте кода показано, как читать электронные письма с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **Список сообщений**
Список сообщений электронной почты в почтовом ящике Exchange можно получить, позвонив в [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) метод. Получите базовую информацию о сообщениях, такую как тема, от кого и идентификатор сообщения, используя [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method.
### **Простой список сообщений**
Чтобы вывести список сообщений в почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Позвоните [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) метод получения коллекции сообщений.
1. Просмотрите коллекцию и отобразите информацию о сообщениях.

В следующем фрагменте кода показано, как подключиться к серверу Exchange с помощью EWS, и перечислены сообщения из папки «Входящие».



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **Список сообщений из разных папок**
В приведенном выше фрагменте кода перечислены все сообщения в папке «Входящие». Можно также получить список сообщений из других папок. [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) метод принимает URI папки в качестве параметра. Если URI папки действителен, вы можете получить список сообщений из этой папки. Используйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->Свойство xxxFolderUri для получения URI разных папок. В остальном код такой же, как и при получении списка сообщений. В следующем фрагменте кода показано, как составить список сообщений из разных папок с помощью EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Список сообщений с поддержкой пейджинга**
В следующем фрагменте кода показано, как получить список сообщений с поддержкой пейджинга.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Получение информации о типе сообщения из ExchangeMessageInfo**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}
## **Сохранение сообщений**
В этой статье показано, как получать сообщения из почтового ящика Exchange Server и сохранять их на диск в форматах EML и MSG:

- Сохранить как EML на диске.
- Сохранить в потоке памяти.
- Сохранить как MSG.
### **Сохранение сообщений в EML**
Чтобы получать сообщения и сохранять их в формате EML, выполните следующие действия:

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Укажите URI почтового ящика, имя пользователя, пароль и домен.
1. Позвоните [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) метод получения экземпляра [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection.
1. Пройдите через [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) коллекция для получения уникального URI для каждого сообщения.
1. Позвоните [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) метод и передайте уникальный URI и сохраните местоположение в качестве параметров.

В следующем фрагменте кода показано, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}
### **Сохранение сообщений в потоке памяти**
Вместо сохранения файлов EML на диск можно сохранить их в потоке памяти. Это удобно, если вы хотите сохранить поток в каком-либо месте хранения, например в базе данных. Как только поток будет сохранен в базе данных, вы можете перезагрузить файл EML в [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) класс. В следующем фрагменте кода показано, как сохранять сообщения из почтового ящика Exchange Server в поток памяти с помощью EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}
### **Сохранение сообщений в формате MSG**
The [IEWSClient->SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) метод может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) метод, который возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) класс. Затем позвоните [MailMessage->Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) метод сохранения сообщения в MSG. В следующем фрагменте кода показано, как получать сообщения из почтового ящика Exchange Server и сохранять их в формате MSG с помощью EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}
## **Получение сведений о сообщениях Exchange из URI сообщения**
Сообщение электронной почты представлено уникальным идентификатором (URI) и является неотъемлемой частью объекта ExchangeMessageInfo. Если доступен только URI сообщения, то [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) объект также можно получить, используя эту доступную информацию. Версия, предназначенная для перегрузки [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) принимает список идентификаторов и возвращает [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) коллекция. В следующем фрагменте кода показано, как получить [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) из URI сообщения.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}
## **Получение сообщений из почтового ящика сервера Exchange**
The [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) метод используется для получения списка сообщений из почтового ящика Exchange Server. [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) метод получает основную информацию о сообщениях, например тему, идентификатор сообщения, от и до. Чтобы получить полную информацию о сообщении, Aspose.Email предоставляет [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) метод. Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) класс. [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) Затем класс предоставляет сведения о сообщении, такие как текст, заголовки и вложения. Чтобы получить сообщения из почтового ящика сервера Exchange, выполните следующие действия:

1. Создайте экземпляр типа [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Call [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) метод получения [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Пройдите через [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) коллекция, которую можно получить [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) values.
1. Call [IEWSClient->FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) и сдай [ExchangeMessageInfo->get_UniqueUri()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) в качестве параметра.

Следующий фрагмент кода демонстрирует получение всех сообщений с помощью EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}
## **Размер сообщения перед выборкой**
Microsoft Outlook InterOp предоставляет возможность получения размера сообщения до фактической загрузки всего сообщения с сервера. В случае Aspose.Email API сводная информация, полученная с сервера Exchange, представлена в виде [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) класс. Он предоставляет возможность получения размера сообщения с помощью [Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a) имущество. Чтобы узнать размер сообщения, стандартным вызовом [IEWSClient->ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) используется для извлечения [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). В следующем фрагменте кода показано, как отображать размер сообщения с помощью [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}
## **Загрузка сообщений из общедоступных папок**
Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте Aspose.Email [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Перемещение сообщений**
Вы можете перемещать сообщения электронной почты из одной папки в другую с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод класса Move. Он принимает следующие параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI целевой папки.
### **Перемещение сообщений между папками**
В следующем фрагменте кода показано, как переместить сообщение в почтовом ящике из папки «Входящие» в папку «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, удовлетворяющие заданному условию, в обработанную папку.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}
## **Удаление сообщений**
Вы можете удалить сообщения электронной почты из папки с помощью [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1) метод. В качестве параметра он принимает уникальный URI сообщения.

В следующем фрагменте кода показано, как удалить сообщение из папки «Входящие». Для целей данного примера используется следующий код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывайте сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удаляет сообщение.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}
## **Копирование сообщений**
Aspose.Email API позволяет копировать сообщение из одной папки в другую с помощью [IEWSClient->CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f) метод. Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.
### **Копирование сообщения в другую папку**
В следующем фрагменте кода показано, как скопировать сообщение в другую папку.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}
