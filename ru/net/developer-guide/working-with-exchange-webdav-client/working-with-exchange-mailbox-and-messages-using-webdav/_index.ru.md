---
title: "Работа с почтовым ящиком и сообщениями Exchange с помощью WebDAV"
url: /ru/net/working-with-exchange-mailbox-and-messages-using-webdav/
weight: 20
type: docs
---


## **Получение сведений о почтовом ящике с помощью WebDAV**
The [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) класс содержит элементы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange путем вызова [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) метод. Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Получайте информацию о почтовом ящике из таких объектов, как [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri), и [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). В этой статье показано, как получить доступ к данным почтового ящика непосредственно с сервера Exchange.

Чтобы получить информацию о почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Укажите сервер Exchange, имя пользователя, пароль и домен в поле [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) constructor.
1. Позвоните [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) метод получения размера почтового ящика.
1. Позвоните [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) метод получения экземпляра [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) class.
1. Получите информацию о почтовом ящике с помощью [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) различные свойства класса.

В следующем фрагменте кода показано, как получить информацию о почтовом ящике Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Отправка сообщений электронной почты**
Вы можете отправлять сообщения электронной почты с помощью сервера Exchange с помощью инструментов Aspose.Email.Exchange. [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) метод принимает [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) экземпляр в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять сообщения электронной почты с помощью сервера Exchange.
### **Отправка сообщений электронной почты с помощью сервера Exchange**
Чтобы отправить электронные письма с помощью сервера Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Создайте экземпляр [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Укажите откуда, куда, тему и прочее [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) properties.
1. Позвоните [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) способ отправки электронного письма.

В следующем фрагменте кода показано, как отправлять сообщения электронной почты с помощью Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Чтение писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, а некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей с помощью Aspose.Email for .NET. Этот API предоставляет механизм доступа к папкам и электронным письмам из других почтовых ящиков с помощью [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) класс. Эта функциональность может быть достигнута с помощью перегруженных [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) метод и указание адреса электронной почты пользователя в качестве параметра.

В следующем фрагменте кода показано, как использовать [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) класс для доступа к другому почтовому ящику.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Список сообщений**
Список сообщений электронной почты в почтовом ящике Exchange можно получить, позвонив в [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод. Получите базовую информацию о сообщениях, такую как тема, от кого и идентификатор сообщения, используя [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method.
### **Простой список сообщений**
Чтобы вывести список сообщений в почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Позвоните [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод и создайте коллекцию сообщений.
1. Просмотрите коллекцию и отобразите информацию о сообщениях.

В следующем фрагменте кода показано, как подключиться к почтовому ящику Exchange и получить список сообщений из папки «Входящие».



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Список сообщений из разных папок**
В приведенных выше фрагментах кода перечислены все сообщения в папке «Входящие». Можно также получить список сообщений из других папок. [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод принимает URI папки в качестве параметра. Если URI папки действителен, вы можете получить список сообщений из этой папки. Используйте свойство ExchangeClient.MailboxInfo.xxxFolderURI для получения URI различных папок. В остальном код аналогичен получению списка сообщений. В следующем фрагменте кода показано, как вывести список сообщений из разных папок с помощью [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Список сообщений по идентификатору**
В приведенном выше фрагменте кода использовался [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод для перечисления всех сообщений в указанной папке почтового ящика Exchange Server. Если вы заранее знаете идентификатор сообщения, вы можете получить его с помощью [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid) метод. Чтобы получить сообщение, передайте URI папки и идентификатор сообщения. Этот сценарий полезен, если идентификатор сообщения уже известен, например, когда идентификаторы сообщений сохраняются в базе данных. В следующем фрагменте кода показано, как отображать сообщения по идентификатору.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Сохранение сообщений**
В этом разделе показано, как получать сообщения из почтового ящика Exchange Server и сохранять их на диск в форматах EML и MSG:

- Сохранить как EML на диске.
- Сохранить в потоке памяти.
- Сохранить как MSG.
### **Сохранение сообщений в EML**
Чтобы получать сообщения и сохранять их в формате EML, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Позвоните [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод получения экземпляра [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) collection.
1. Пройдите через [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) коллекция для получения уникального URI для каждого сообщения.
1. Позвоните [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) метод и передайте уникальный URI в качестве параметра.
1. Предоставьте [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) метод с указанием пути к месту сохранения файла.

В следующем фрагменте кода показано, как сохранять сообщения в EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Сохранение сообщений в потоке памяти**
Вместо сохранения файлов EML на диск можно сохранить их в потоке памяти. Это удобно, если вы хотите сохранить поток в каком-либо месте хранения, например в базе данных. Как только поток будет сохранен в базе данных, вы можете перезагрузить файл EML в [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) класс. В следующем фрагменте кода показано, как сохранять сообщения из почтового ящика Exchange Server в поток памяти.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Сохранение сообщений в формате MSG**
The [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) метод может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) метод, который возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) класс. Затем позвоните [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) метод сохранения сообщения в MSG. В следующем фрагменте кода показано, как получать сообщения из почтового ящика Exchange Server и сохранять их в формате MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Получение сообщений из почтового ящика сервера Exchange**
При перечислении сообщений на сервере Exchange использовалось [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод получения списка сообщений из почтового ящика Exchange Server. [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) метод получает основную информацию о сообщениях, например тему, идентификатор сообщения, от и до. Чтобы получить полную информацию о сообщении, Aspose.Email.Exchange предоставляет [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) метод. Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) класс. [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) Затем класс предоставляет сведения о сообщении, такие как текст, заголовки и вложения. Чтобы получить сообщения из почтового ящика сервера Exchange, выполните следующие действия:

1. Создайте экземпляр типа [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Укажите URI почтового ящика, имя пользователя, пароль и домен.
1. Call [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) чтобы получить [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Пройдите через [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) коллекция, которую можно получить [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) values.
1. Call [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) и сдай  [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) в качестве параметра.

В следующем фрагменте кода показано, как вы подключаетесь к почтовому ящику Exchange Server и получаете все сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Размер сообщения перед выборкой**
Microsoft Outlook InterOp предоставляет возможность получения размера сообщения до фактической загрузки всего сообщения с сервера. В случае Aspose.Email API сводная информация, полученная с сервера Exchange, представлена в виде [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) класс. Он предоставляет ту же функцию, что и получение размера сообщения с помощью свойства Size. Чтобы узнать размер сообщения, стандартным вызовом ExchangeClient [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) используется для получения коллекции [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). В следующем фрагменте кода показано, как отображать размер сообщения с помощью [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) class.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Перемещение сообщений**
Вы можете перемещать сообщения электронной почты из одной папки в другую с помощью [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index) метод. Он принимает следующие параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI целевой папки.
### **Перемещение сообщений между папками**
В следующем фрагменте кода показано, как переместить сообщение в почтовом ящике из папки «Входящие» в папку «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, удовлетворяющие заданному условию, в обработанную папку.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Удаление сообщений**
Вы можете удалить сообщения электронной почты из папки с помощью [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index) метод. В качестве параметра он принимает уникальный URI сообщения.
### **Удаление сообщений с сервера Exchange**
В следующем фрагменте кода показано, как удалить сообщение из папки «Входящие». Для целей данного примера используется следующий код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывайте сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удалите сообщение.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}
