---
title: Работа с почтовыми ящиками Exchange и сообщениями с помощью WebDav
type: docs
weight: 20
url: /net/working-with-exchange-mailbox-and-messages-using-webdav/
---


## **Получение информации о почтовом ящике с помощью WebDav**
Класс [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) имеет методы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange, вызывая метод [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index). Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Получите информацию о почтовом ящике из таких свойств, как [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri) и [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). В этой статье показано, как получить информацию о почтовом ящике непосредственно с сервера Exchange.

Чтобы получить информацию о почтовом ящике Exchange:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Укажите сервер Exchange, имя пользователя, пароль и домен в конструкторе [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Вызовите метод [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) для получения размера почтового ящика.
1. Вызовите метод [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) для получения экземпляра класса [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).
1. Получите информацию о почтовом ящике, используя различные свойства класса [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).

Следующий фрагмент кода демонстрирует, как получить информацию о почтовом ящике Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Отправка электронных сообщений**
Вы можете отправлять электронные сообщения с помощью сервера Exchange с помощью инструментов Aspose.Email.Exchange. Метод [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) принимает экземпляр [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять электронные сообщения с использованием сервера Exchange.
### **Отправка электронных сообщений с помощью сервера Exchange**
Чтобы отправить электронные письма с использованием сервера Exchange:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Создайте экземпляр класса [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Укажите свойства от, до, тему и другие свойства [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Вызовите метод [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) для отправки электронной почты.

Следующий фрагмент кода демонстрирует, как отправлять электронные сообщения с использованием сервера Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Чтение электронных писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, и некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей с помощью Aspose.Email для .NET. Этот API предоставляет механизм для доступа к папкам и электронным письмам из других почтовых ящиков с помощью класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Эта функциональность может быть достигнута с помощью перегруженного метода [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) и предоставления адреса электронной почты пользователя в качестве параметра.

Следующий фрагмент кода демонстрирует, как использовать класс [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) для доступа к другому почтовому ящику.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Перечисление сообщений**
Список электронных сообщений в почтовом ящике Exchange можно получить, вызвав метод [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index). Получите основную информацию о сообщениях, такую как тема, от, до и идентификатор сообщения, с помощью метода [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index).
### **Простое перечисление сообщений**
Чтобы перечислить сообщения в почтовом ящике Exchange:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Вызовите метод [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) и создайте коллекцию сообщений.
1. Пройдите по коллекции и отобразите информацию о сообщении.

Следующий фрагмент кода демонстрирует, как подключиться к почтовому ящику Exchange и получить список сообщений из папки "Входящие".



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Перечисление сообщений из разных папок**
В приведенных выше фрагментах кода перечислены все сообщения в папке "Входящие". Также можно получить список сообщений из других папок. Метод [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) принимает URI папки в качестве параметра. Пока URI папки действителен, вы можете получить список сообщений из этой папки. Используйте свойство ExchangeClient.MailboxInfo.xxxFolderUri, чтобы получить URI различных папок. Остальная часть кода такая же, как для получения списка сообщений. Следующий фрагмент кода демонстрирует, как перечислить сообщения из разных папок, используя [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Перечисление сообщений по ID**
В приведенном выше фрагменте кода использован метод [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) для перечисления всех сообщений в указанной папке почтового ящика сервера Exchange. Если вы заранее знаете идентификатор сообщения, вы можете получить сообщение, используя метод [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid). Чтобы получить сообщение, передайте URI папки и идентификатор сообщения. Этот сценарий полезен, когда вы уже знаете идентификатор сообщения, например, когда идентификаторы сообщений сохранены в базе данных. Следующий фрагмент кода демонстрирует, как перечислить сообщения по ID.


{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Сохранение сообщений**
Эта тема показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их на диск в форматах EML и MSG:

- Сохранить в формате EML на диск.
- Сохранить в поток памяти.
- Сохранить в формате MSG.
### **Сохранение сообщений в формате EML**
Чтобы получить сообщения и сохранить в формате EML:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Вызовите метод [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index), чтобы получить экземпляр коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Пройдите по коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection), чтобы получить уникальный URI для каждого сообщения.
1. Вызовите метод [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) и передайте уникальный URI в качестве параметра.
1. Передайте методу [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) путь, по которому вы хотите сохранить файл.

Следующий фрагмент кода демонстрирует, как сохранить сообщения в формате EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Сохранение сообщений в поток памяти**
Вместо того чтобы сохранять файлы EML на диск, можно сохранить их в поток памяти. Это полезно, когда вы хотите сохранить поток в какое-то место хранения, например, в базе данных. После того как поток был сохранен в базе данных, вы можете повторно загрузить файл EML в класс [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage). Следующий фрагмент кода демонстрирует, как сохранить сообщения из почтового ящика сервера Exchange в поток памяти.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Сохранение сообщений в формате MSG**
Метод [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите метод [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage), который возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Затем вызовите метод [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index), чтобы сохранить сообщение в формате MSG. Следующий фрагмент кода показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их в формате MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Получение сообщений из почтового ящика сервера Exchange**
Метод [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) использовался для получения списка сообщений из почтового ящика сервера Exchange. Метод [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) получает основную информацию о сообщениях, например, тему, идентификатор сообщения, от и до. Чтобы получить полные детали сообщения, Aspose.Email.Exchange предоставляет метод [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Класс [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) затем предоставляет такие детали сообщения, как тело, заголовки иAttachments. Чтобы получить сообщения из почтового ящика сервера Exchange:

1. Создайте экземпляр типа [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Укажите mailboxUri, имя пользователя, пароль и домен.
1. Вызовите [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index), чтобы получить [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Пройдите по коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection), чтобы получить значения [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri).
1. Вызовите [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) и передайте  [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) в качестве параметра.

Следующий фрагмент кода показывает, как подключиться к почтовому ящику сервера Exchange и получить все сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Предварительное получение размера сообщения**
Microsoft Outlook InterOp предоставляет возможность извлекать размер сообщения до фактической выборки полного сообщения с сервера. В случае API Aspose.Email сводная информация, полученная с сервера Exchange, представлена классом [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). Он предоставляет ту же функцию получения размера сообщения с помощью свойства Size. Для получения размера сообщения используется стандартный вызов метода [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) класса ExchangeClient, который получает коллекцию [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). Следующий фрагмент кода показывает, как отобразить размер сообщения с помощью класса [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Перемещение сообщений**
Вы можете перемещать электронные сообщения из одной папки в другую с помощью метода класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index). Он принимает параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI папки назначения.
### **Перемещение сообщений между папками**
Следующий фрагмент кода демонстрирует, как переместить сообщение в почтовом ящике из папки "Входящие" в папку под названием "Обработано". В этом примере приложение:

1. Читает сообщения из папки "Входящие".
1. Обрабатывает некоторые сообщения на основе определенных критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, которые соответствуют указанному условию, в папку "обработано".



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Удаление сообщений**
Вы можете удалить электронные сообщения из папки с помощью метода класса [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index). Он принимает уникальный URI сообщения в качестве параметра.
### **Удаление сообщений с сервера Exchange**
Следующий фрагмент кода демонстрирует, как удалить сообщение из папки "Входящие". Для целей этого примера код:

1. Читает сообщения из папки "Входящие".
1. Обрабатывает сообщения на основе определенных критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удаляет сообщение.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}