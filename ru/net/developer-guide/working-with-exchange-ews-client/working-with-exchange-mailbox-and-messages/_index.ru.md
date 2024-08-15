---
title: "Работа с почтовым ящиком и сообщениями Exchange — чтение электронной почты с сервера Exchange на языке C#"
url: /ru/net/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Работа с почтовым ящиком и сообщениями Exchange"
keywords: "c# — чтение электронной почты с сервера обмена"
---


## **Получение данных почтового ящика с помощью EWS**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс содержит элементы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange путем вызова [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/) метод. Он возвращает экземпляр типа [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Получайте информацию о почтовом ящике из таких объектов, как [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) and [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). В этой статье показано, как получить доступ к данным почтового ящика с помощью веб-служб Exchange.

Если вы хотите подключиться к серверу Exchange с помощью веб-служб Exchange (EWS), используйте [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) класс в пространстве имен Aspose.Email.Exchange. Этот класс использует EWS для подключения к элементам на сервере Exchange и управления ими. В следующем фрагменте кода на C# показано, как получать информацию о почтовом ящике с помощью веб-служб Exchange.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials        
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
Console.WriteLine("Mailbox size: " + client.GetMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
Console.WriteLine("Inbox folder URI: " + mailboxInfo.InboxUri);
Console.WriteLine("Sent Items URI: " + mailboxInfo.SentItemsUri);
Console.WriteLine("Drafts folder URI: " + mailboxInfo.DraftsUri);
```

## **Отправка сообщений электронной почты**

Вы можете отправлять сообщения электронной почты с помощью Exchange Server с помощью инструментов в [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) метод принимает [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять сообщения электронной почты с помощью веб-служб Exchange.

Aspose.Email предоставляет [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. В следующем фрагменте кода показано, как использовать EWS для отправки электронных писем с помощью Microsoft Exchange Server. В следующем фрагменте кода на C# показано, как отправлять сообщения электронной почты с помощью EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@ domain.com ";
msg.Subject = "Sending message from exchange server";
msg.HtmlBody = "<h3>sending message from exchange server</h3>";

// Send the message
client.Send(msg);
```

## **Uri получаемого отправленного товара**

Идентификатор отправленного электронного письма можно получить с сервера Exchange с помощью следующего примера кода:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Register the event handler
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "test message", "This is a test message");

    client.Send(eml);
}
```

где метод делегата:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Define an event handler method
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
   
    // Now we can get an id of sent email, which was saved in Sent Items folder
    string id = e.SentFolderItemId;
}
```

## **Чтение писем из почтового ящика другого пользователя**

Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, а некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей с помощью Aspose.Email for .NET. Этот API предоставляет механизм доступа к папкам и электронным письмам из других почтовых ящиков с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods) интерфейс. Эта функциональность может быть достигнута с помощью перегруженных [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) метод и указание адреса электронной почты пользователя в качестве параметра.

В следующем фрагменте кода C# показано, как читать электронные письма с помощью класса IEWSClient.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Список сообщений**

Список сообщений электронной почты в почтовом ящике Exchange можно получить, позвонив в [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод. Получите базовую информацию о сообщениях, такую как тема, откуда, куда и идентификатор сообщения, используя метод listMessage.

### **Простой список сообщений**

Чтобы вывести список сообщений в почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод и создайте коллекцию сообщений.
1. Просмотрите коллекцию и отобразите информацию о сообщениях.

В следующем фрагменте кода C# показано, как подключиться к серверу Exchange с помощью EWS и вывести список сообщений из папки «Входящие».

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Пройдите через collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message ID: " + msgInfo.MessageId);
    Console.WriteLine("Unique URI: " + msgInfo.UniqueUri);
}
```

### **Список сообщений из разных папок**

[Вышеуказанные фрагменты кода](#simple-messages-listing) перечислите все сообщения в папке «Входящие». Также можно получить список сообщений из других папок. [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод принимает URI папки в качестве параметра. Если URI папки действителен, вы можете получить список сообщений из этой папки. Используйте [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties) свойство для получения URI разных папок. В остальном код такой же, как и при получении списка сообщений. В следующем фрагменте кода показано, как составить список сообщений из разных папок с помощью EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **Список сообщений с поддержкой пейджинга**

В следующем фрагменте кода показано, как получить список сообщений с поддержкой пейджинга.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Move paging parameters to separate class");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Total Pages Count
        Console.WriteLine(pageInfo.TotalCount);

        pages.Add(pageInfo);
        while (!pageInfo.LastPage)
        {
            pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage, pageInfo.PageOffset + 1);
            pages.Add(pageInfo);
        }
        int retrievedItems = 0;
        foreach (ExchangeMessagePageInfo pageCol in pages)
            retrievedItems += pageCol.Items.Count;
        // Verify total message count using paging
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}         
```

### **Получение информации о типе сообщения из ExchangeMessageInfo**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @"";
const string username = @"username@ASE305.onmicrosoft.com";
const string password = @"password";
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```
### **Получение класса сообщений из объекта ExchangeMessageInfo**

Класс сообщений представляет тип элемента в хранилище Exchange. Получив класс сообщений, вы можете определить тип сообщения электронной почты Exchange и выполнить определенные операции на основе его классификации.

Ниже приведен пример получения класса сообщений с использованием [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) класс Aspose.Email для .NET:

**Пример кода**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Message Class: {0}", messageInfo.MessageClass);
    }
}
```

## **Сохранение сообщений**

В этой статье показано, как получать сообщения из почтового ящика Exchange Server и сохранять их на диск в форматах EML и MSG:

- Сохранить как EML на диске.
- Сохранить в потоке памяти.
- Сохранить как MSG.
 
### **Сохранение сообщений в EML**

Чтобы получать сообщения и сохранять их в формате EML, выполните следующие действия:

1. Создайте экземпляр [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Укажите URI почтового ящика, имя пользователя, пароль и домен.
1. Позвоните [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод получения экземпляра [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/).
1. Пройдите через [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/) чтобы получить уникальный URI для каждого сообщения.
1. Позвоните [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) метод и передайте уникальный URI в качестве параметра.
1. Предоставьте в [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) метод с указанием пути к месту сохранения файла.

В следующем фрагменте кода показано, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Create instance of IEWSClient interface by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Пройдите через collection получить Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in disk
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Сохранение сообщений в потоке памяти**

Вместо сохранения файлов EML на диск можно сохранить их в потоке памяти. Это удобно, если вы хотите сохранить поток в каком-либо месте хранения, например в базе данных. Как только поток будет сохранен в базе данных, вы можете перезагрузить файл EML в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. В следующем фрагменте кода показано, как сохранять сообщения из почтового ящика Exchange Server в поток памяти с помощью EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string datadir = RunExamples.GetDataDir_Exchange();
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Пройдите через collection получить Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in memory stream
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, datadir + stream);
}
```

### **Сохранение сообщений в формате MSG**

The [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) метод может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) метод, который возвращает экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Затем позвоните [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод сохранения сообщения в MSG. В следующем фрагменте кода показано, как получать сообщения из почтового ящика Exchange Server и сохранять их в формате MSG с помощью EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Пройдите через collection получить Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
   
    // Now get the message details using FetchMessage() and Save message as Msg
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Получение сведений о сообщениях Exchange из URI сообщения**

Сообщение электронной почты представлено уникальным идентификатором, URI, и является неотъемлемой частью [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) объект. В случае, если доступен только URI сообщения, тогда [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) объект также можно получить, используя эту доступную информацию. Версия, предназначенная для перегрузки [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) принимает список идентификаторов для использования [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). В следующем фрагменте кода показано, как получить [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) из URI сообщения.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Do something ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

## **Получение сообщений из почтового ящика сервера Exchange**

Для перечисления сообщений на сервере Exchange [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод используется для получения списка сообщений из почтового ящика Exchange Server. [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) метод получает основную информацию о сообщениях, например тему, идентификатор сообщения, от и до. Чтобы получить полную информацию о сообщении, Aspose.Email.Exchange предоставляет [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) метод. Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) Затем класс предоставляет сведения о сообщении, такие как текст, заголовки и вложения. Узнайте больше об API MailMessage или узнайте, как управлять электронной почтой с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Чтобы получить сообщения из почтового ящика сервера Exchange, выполните следующие действия:

1. Создайте экземпляр типа [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) чтобы получить [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
1. Пройдите через [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) получить [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) values.
1. Call [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) и сдай [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) в качестве параметра.

В следующем фрагменте кода показано, как вы подключаетесь к почтовому ящику Exchange Server и получаете все сообщения с помощью EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Пройдите через collection получить Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Now get the message details using FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);

    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Attachment Name: " + att.Name);
 }
}
```

### **Использование метода fetchItem для получения сообщения**

{{% alert color="primary" %}}

Обратите внимание, [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) метод возвращает сообщение без вложений. Для получения сообщений с вложениями используйте [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) метод, описанный в разделе ниже.

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/fetchitem) метод более предпочтителен, если вы хотите получить [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) и работайте со свойствами MAPI. Вы также можете использовать этот метод для извлечения любых элементов Outlook, таких как контакт, встреча, задача и т. д.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Contacts folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Пройдите через collection получить Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Now get the message using FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Использование метода fetchItems**

Описанное выше [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) метод возвращает сообщение **без вложений**, в попытке сохранить производительность.

Для получения сообщений с вложениями используйте более мощный [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) метод, позволяющий передать [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/) options.

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

## **Загрузка товаров с помощью вложений**

The [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)(параметры ewsFetchItems) метод EWSClient извлекает элементы электронной почты с сервера Exchange. Он принимает экземпляр [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) класс в качестве параметра для определения различных вариантов выборки элементов.

В следующем коде показано, как получить элементы с вложениями:

```cs
// Позвоните ListMessages method to retrieve a list of message from the Inbox folder
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Создайте экземпляр EwsFetchItems class and assign it to the options variable
var options = EwsFetchItems.Create();

// Generate a new collection of messages which is then converted to a List.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Fetch only messages containing attachments
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

## **Размер сообщения перед выборкой**

Microsoft Outlook InterOp предоставляет возможность получения размера сообщения до фактической загрузки всего сообщения с сервера. В случае Aspose.Email API сводная информация, полученная с сервера Exchange, представлена в виде [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) класс. Он предоставляет ту же функцию получения размера сообщения с помощью [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/) имущество. Чтобы узнать размер сообщения, стандартным вызовом [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) используется для получения коллекции [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). В следующем фрагменте кода показано, как отображать размер сообщения с помощью [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Пройдите через collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message Size: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

## **Рекурсивная загрузка сообщений**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) метод можно использовать для рекурсивного получения сообщений из папок и подпапок из почтового ящика Exchange Server. Для этого требуется Exchange Server 2007 или более поздними версиями, поскольку в нем используется EWS. В следующем фрагменте кода показано, как загрузить весь почтовый ящик (папки и подпапки) сервера Exchange. Структура папок создается локально, и все сообщения загружаются.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Register callback method for SSL validation event
    ServicePointManager.ServerCertificateValidationCallback += RemoteCertificateValidationHandler;
    try
    {
        DownloadAllMessages();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void DownloadAllMessages()
{
    try
    {
        string rootFolder = domain + "-" + username;
        Directory.CreateDirectory(rootFolder);
        string inboxFolder = rootFolder + "\\Inbox";
        Directory.CreateDirectory(inboxFolder);

        Console.WriteLine("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Позвоните recursive method to read messages and get sub-folders
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("All messages downloaded.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Recursive method получить messages from folders and sub-folders
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Create the folder in disk (same name as on IMAP server)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Listing messages....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Get subject and other properties of the message
        Console.WriteLine("Subject: " + msgInfo.Subject);

        // Get rid of characters like ? and :, which should not be included in a file name
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
 
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // If this folder has sub-folders, call this method recursively получить messages
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        foreach (ExchangeFolderInfo subfolderInfo in folderInfoCollection)
        {
            ListMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    }
    catch (Exception)
    {
    }
}
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // Ignore the checks and go ahead
}
```

## **Загрузка сообщений из общедоступных папок**

Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static string dataDir = RunExamples.GetDataDir_Exchange();
public static string mailboxUri = "https://exchange/ews/exchange.asmx"; // EWS
public static string username = "administrator";
public static string password = "pwd";
public static string domain = "ex2013.local";

public static void Run()
{
    try
    {
        ReadPublicFolders();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void ReadPublicFolders()
{
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.ListPublicFolders();
    foreach (ExchangeFolderInfo publicFolder in folders)
    {
        Console.WriteLine("Name: " + publicFolder.DisplayName);
        Console.WriteLine("Subfolders count: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);

    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Folder Name: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir +  msg.Subject + ".msg",  SaveOptions.DefaultMsgUnicode);
    }

    // Call this method recursively for any subfolders
    if (publicFolder.ChildFolderCount > 0)
    {
        ExchangeFolderInfoCollection subfolders = client.ListSubFolders(publicFolder);
        foreach (ExchangeFolderInfo subfolder in subfolders)
        {
            ListMessagesFromSubFolder(subfolder, client);
        }
    }
}
```

## **Перемещение сообщений**

Вы можете перемещать сообщения электронной почты из одной папки в другую с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/) метод. Он принимает следующие параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI целевой папки.
 
### **Перемещение сообщений между папками**

В следующем фрагменте кода показано, как переместить сообщение в почтовом ящике из папки «Входящие» в папку «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, удовлетворяющие заданному условию, в обработанную папку.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("process this message") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Message moved...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Удаление сообщений**

Вы можете удалить сообщения электронной почты из папки с помощью [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/exchangeclient/) class [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) метод. В качестве параметра он принимает уникальный URI сообщения.

В следующем фрагменте кода показано, как удалить сообщение из папки «Входящие». Для целей данного примера используется следующий код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удаляет сообщение.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
           
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Delete message based on some criteria
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("delete") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Message deleted...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Копирование сообщений**

Aspose.Email API позволяет копировать сообщение из одной папки в другую, используя [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/) метод. Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.

### **Копирование сообщения в другую папку**

В следующем фрагменте кода показано, как скопировать сообщение в другую папку.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```
