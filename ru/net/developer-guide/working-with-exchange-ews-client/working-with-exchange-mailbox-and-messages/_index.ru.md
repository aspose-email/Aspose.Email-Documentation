---
title: "Работа с почтовыми ящиками и сообщениями Exchange - Чтение электронной почты с сервера Exchange на C#"
url: /ru/net/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Работа с почтовыми ящиками и сообщениями Exchange"
keywords: "c# чтение электронной почты с сервера exchange"
---

## **Получение информации о почтовом ящике с использованием EWS**

Класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) имеет методы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange, вызывая метод [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/). Он возвращает экземпляр типа [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Получите информацию о почтовом ящике из свойств, таких как [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) и [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). Эта статья показывает, как получить доступ к информации о почтовом ящике с помощью Exchange Web Services.

Если вы хотите подключиться к серверу Exchange, используя Exchange Web Services (EWS), используйте класс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) в пространстве имен Aspose.Email.Exchange. Этот класс использует EWS для подключения и управления элементами на сервере Exchange. Следующий фрагмент кода на C# показывает, как получить информацию о почтовом ящике с помощью веб-служб обмена.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса EWSClient, указав учетные данные         
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить размер почтового ящика, информацию о почтовом ящике Exchange, URI для почтового ящика и папки "Входящие"
Console.WriteLine("Размер почтового ящика: " + client.GetMailboxSize() + " байт");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("URI почтового ящика: " + mailboxInfo.MailboxUri);
Console.WriteLine("URI папки «Входящие»: " + mailboxInfo.InboxUri);
Console.WriteLine("URI отправленных элементов: " + mailboxInfo.SentItemsUri);
Console.WriteLine("URI папки «Черновики»: " + mailboxInfo.DraftsUri);
```

## **Отправка электронных сообщений**

Вы можете отправлять электронные сообщения, используя сервер Exchange с помощью инструментов в [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). Метод [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) принимает экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) в качестве параметра и отправляет электронное письмо. Эта статья объясняет, как отправлять электронные сообщения, используя веб-службы Exchange.

Aspose.Email предоставляет класс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) для подключения к Microsoft Exchange Server с помощью веб-служб Exchange. Следующий фрагмент кода показывает, как использовать EWS для отправки электронных писем с Microsoft Exchange Server. Следующий фрагмент кода на C# показывает, как отправлять электронные сообщения, используя EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Создать экземпляр типа MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@domain.com";
msg.Subject = "Отправка сообщения с сервера Exchange";
msg.HtmlBody = "<h3>отправка сообщения с сервера Exchange</h3>";

// Отправить сообщение
client.Send(msg);
```

## **Получение URI отправленного элемента**

Идентификатор отправленного электронного письма можно получить с сервера Exchange с помощью следующего примера кода:

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Зарегистрировать обработчик событий
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "тестовое сообщение", "Это тестовое сообщение");

    client.Send(eml);
}
```

где метод делегата:

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Определить метод-обработчик событий
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
    // Теперь мы можем получить идентификатор отправленного электронного письма, который был сохранен в папке «Отправленные элементы»
    string id = e.SentFolderItemId;
}
```

## **Чтение электронных писем из почтового ящика другого пользователя**

Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, и некоторые пользователи имеют несколько учетных записей электронной почты на одном и том же сервере Exchange. В обоих случаях пользователи могут получать доступ к почтовым ящикам других пользователей, используя Aspose.Email для .NET. Этот API предоставляет механизм доступа к папкам и письмам из других почтовых ящиков с использованием интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods). Эта функция может быть реализована, используя перегруженный метод [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) и предоставляя адрес электронной почты пользователя в качестве параметра.

Следующий фрагмент кода на C# показывает, как читать электронные письма с использованием класса IEWSClient.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить информацию о почтовом ящике Exchange для другой учетной записи электронной почты
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Список сообщений**

Список email сообщений в почтовом ящике Exchange можно получить, вызвав метод [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). Получите основную информацию о сообщениях, такую как тема, от, к и идентификатор сообщения, используя метод ListMessage.

### **Простой список сообщений**

Чтобы перечислить сообщения в почтовом ящике Exchange:

1. Создайте экземпляр интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) и создайте коллекцию сообщений.
1. Переберите коллекцию и отобразите информацию о сообщении.

Следующий фрагмент кода на C# показывает, как подключиться к серверу Exchange, используя EWS, и перечислить сообщения из папки "Входящие".

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из папки «Входящие»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Переберите коллекцию, чтобы отобразить основную информацию
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Тема: " + msgInfo.Subject);
    Console.WriteLine("От: " + msgInfo.From.ToString());
    Console.WriteLine("Кому: " + msgInfo.To.ToString());
    Console.WriteLine("Идентификатор сообщения: " + msgInfo.MessageId);
    Console.WriteLine("Уникальный URI: " + msgInfo.UniqueUri);
}
```

### **Список сообщений из разных папок**

[Вышеуказанные фрагменты кода](#простой-список-сообщений) перечисляют все сообщения в папке «Входящие». Возможно также получить список сообщений из других папок. Метод [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) принимает URI папки в качестве параметра. При условии, что URI папки действителен, вы можете получить список сообщений из этой папки. Используйте свойство [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties), чтобы получить URI различных папок. Остальная часть кода такая же, как и для получения списка сообщений. Следующий фрагмент кода показывает, как перечислить сообщения из различных папок, используя EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить URI папки
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Получить список сообщений из указанной папки
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **Список сообщений с поддержкой постраничного вывода**

Следующий фрагмент кода показывает, как получить список сообщений с поддержкой постраничного вывода.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Создайте несколько тестовых сообщений, чтобы добавить их на сервер для последующего извлечения
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Переместите параметры постраничной навигации в отдельный класс");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Проверьте, что сообщения были добавлены на сервер
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// ПОЛУЧЕНИЕ СООБЩЕНИЙ С ИСПОЛЬЗОВАНИЕМ ПОДДЕРЖКИ ПОСТРАНИЧНОГО ВЫВОДА ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Общее количество страниц
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
        // Проверьте общее количество сообщений с помощью постраничного вывода
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}          
```

### **Получение информации о типе сообщения из ExchangeMessageInfo**

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @""; 
const string username = @"username@ASE305.onmicrosoft.com"; 
const string password = @"password"; 
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```

### **Извлечение класса сообщения из объекта ExchangeMessageInfo**

Класс сообщения представляет тип элемента в хранилище Exchange. Получив класс сообщения, вы можете определить тип электронного письма Exchange и выполнять специфические операции на основе его классификации.

Ниже приведен пример получения класса сообщения с использованием класса [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) из Aspose.Email для .NET:

**Пример кода**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Класс сообщения: {0}", messageInfo.MessageClass);
    }
}
```

## **Сохранение сообщений**

Эта статья показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их на диске в форматах EML и MSG:

- Сохранить как EML на диске.
- Сохранить в память.
- Сохранить как MSG.
  
### **Сохранение сообщений в EML**

Чтобы получить сообщения и сохранить в формате EML:

1. Создайте экземпляр интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
2. Укажите mailboxUri, username, password и domain.
3. Вызовите метод [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) для получения экземпляра [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessagesinfocollection/).
4. Переберите [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessagesinfocollection/) для получения уникального URI для каждого сообщения.
5. Вызовите метод [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) и передайте уникальный URI в качестве параметра.
6. Укажите метод [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) с путем, где вы хотите сохранить файл.

Следующий фрагмент кода показывает, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Создать экземпляр интерфейса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из папки «Входящие»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Переберите коллекцию, чтобы получить URI сообщения
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Теперь сохраните сообщение на диске
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Сохранение сообщений в поток памяти**

Вместо сохранения файлов EML на диске, вы можете сохранить их в поток памяти. Это полезно, когда вы хотите сохранить поток в какое-либо место хранения, например, базу данных. После того как поток был сохранен в базу данных, вы можете загрузить файл EML в класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Следующий фрагмент кода показывает, как сохранить сообщения из почтового ящика сервера Exchange в поток памяти с использованием EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
string datadir = RunExamples.GetDataDir_Exchange();
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из папки «Входящие»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Переберите коллекцию, чтобы получить URI сообщения
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Теперь сохраните сообщение в поток памяти
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, datadir + stream);
}
```

### **Сохранение сообщений в формате MSG**

Метод [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) может непосредственно сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите метод [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/), который возвращает экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Затем вызовите метод [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), чтобы сохранить сообщение в формате MSG. Следующий фрагмент кода показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их в формате MSG с использованием EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызываем метод ListMessages для получения информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Переберите коллекцию, чтобы получить URI сообщения
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
    
    // Теперь получите детали сообщения с помощью FetchMessage() и сохраните сообщение в формате Msg 
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Получение ExchangeMessageInfo из URI сообщения**

Электронное сообщение представлено его уникальным идентификатором, URI, и является неотъемлемой частью объекта [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Если доступен только URI сообщения, то объект [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) также может быть извлечен с использованием этой доступной информации. Перегруженная версия [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) принимает список идентификаторов для использования [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). Следующий фрагмент кода показывает, как получить [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) из URI сообщения.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Сообщения, сохраненные из папки «Отправленные», не содержат поле «Кому»");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Сделать что-то ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

## **Извлечение сообщений из почтового ящика сервера Exchange**

Для перечисления сообщений на сервере Exchange используется метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/), чтобы получить список сообщений из почтового ящика Exchange. Метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) получает основную информацию о сообщениях, например, тему, идентификатор сообщения, от и к. Чтобы получить полные детали сообщения, Aspose.Email.Exchange предоставляет метод [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр класса [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) затем предоставляет такие детали сообщения, как тело, заголовки и вложения. Узнайте больше о MailMessage API или узнайте, как управлять электронными письмами с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Чтобы извлечь сообщения из почтового ящика сервера Exchange:

1. Создайте экземпляр типа [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
2. Укажите имя сервера, имя пользователя, пароль и домен.
3. Вызовите [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/), чтобы получить [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
4. Переберите [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/), чтобы получить значения [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/).
5. Вызовите [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) и передайте [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) в качестве параметра.

Следующий фрагмент кода показывает, как подключиться к почтовому ящику сервера Exchange и извлечь все сообщения, используя EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создайте экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из «Входящих»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Переберите коллекцию, чтобы получить URI сообщения
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Теперь получите детали сообщения, используя FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);
 
    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Имя вложения: " + att.Name);
 }
}
```

### **Использование метода FetchItem для извлечения сообщения**

{{% alert color="primary" %}}

Обратите внимание, что метод [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) возвращает сообщение без вложений. Чтобы извлечь сообщения с вложениями, используйте метод [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/), описанный в следующем разделе.

{{% /alert %}}

Метод [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem) более предпочтителен, если вы хотите извлечь [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) и работать с MAPI-свойствами. Вы также можете использовать этот метод для получения любых элементов Outlook, таких как контакт, событие, задача и т.д.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из папки «Контакты»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Переберите коллекцию, чтобы получить URI сообщения
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Теперь получите сообщение с помощью FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // Если необходимо, вы можете привести MapiMessage к правильному типу элемента, чтобы упростить работу с его свойствами.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Использование метода FetchItems**

Метод [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) возвращает сообщение **без вложений**, чтобы сохранить производительность.

Чтобы получить сообщения с вложениями, используйте более мощный метод [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/), который позволяет передавать параметры [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/) опций.

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

## **Извлечение элементов с вложениями**

Метод [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)(EwsFetchItems options) клиента Ews извлекает email-элементы с сервера Exchange. Он принимает экземпляр класса [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) в качестве параметра для определения различных параметров для извлечения элементов.

Следующий код показывает, как получить элементы с вложениями:

```cs
// Вызовите метод ListMessages, чтобы извлечь список сообщений из папки «Входящие»
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Создайте экземпляр класса EwsFetchItems и назначьте его переменной options
var options = EwsFetchItems.Create();

// Сгенерируйте новую коллекцию сообщений, которая затем будет преобразована в список.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Извлечь только сообщения, содержащие вложения
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

## **Предварительное получение размера сообщения**

Microsoft Outlook InterOp предоставляет возможность извлечения размера сообщения до фактического получения полного сообщения с сервера. В случае API Aspose.Email сводная информация, полученная с сервера Exchange, представлена классом [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Он предоставляет ту же возможность извлечения размера сообщения с помощью свойства [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/). Для получения размера сообщения используется стандартный вызов [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/), который извлекает коллекцию [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Следующий фрагмент кода показывает, как отобразить размер сообщения, используя класс [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/).

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызовите метод ListMessages, чтобы перечислить информацию о сообщениях из папки «Входящие»
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Переберите коллекцию, чтобы отобразить основную информацию
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Тема: " + msgInfo.Subject);
    Console.WriteLine("От: " + msgInfo.From.ToString());
    Console.WriteLine("Кому: " + msgInfo.To.ToString());
    Console.WriteLine("Размер сообщения: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

## **Рекурсивное извлечение сообщений**

Метод [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) можно использовать для получения сообщений из папок и подпапок сервера Exchange почтового ящика рекурсивно. Это требует Exchange Server 2007 или более поздней версии, поскольку он использует EWS. Следующий фрагмент кода показывает, как загрузить весь почтовый ящик (папки и подпапки) сервера Exchange. Структура папок создается локально, и все сообщения загружаются.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Зарегистрировать метод обратного вызова для события проверки SSL
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

        Console.WriteLine("Загрузка всех сообщений из «Входящих»....");
        // Создать экземпляр класса IEWSClient, указав учетные данные
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("URI почтового ящика: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // Перечислить все папки с сервера Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Вызовите рекурсивный метод для чтения сообщений и получения подпапок
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("Все сообщения загружены.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Рекурсивный метод для получения сообщений из папок и подпапок
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Создать папку на диске (с тем же именем, что и на IMAP-сервере)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // Перечислить сообщения
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Список сообщений....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Получить тему и другие свойства сообщения
        Console.WriteLine("Тема: " + msgInfo.Subject);

        // Удалить такие символы, как ? и :, которые не должны быть включены в имя файла
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
  
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // Если у этой папки есть подпапки, вызовите этот метод рекурсивно, чтобы получить сообщения
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
    return true; // Игнорировать проверки и продолжать
}
```

## **Загрузка сообщений из публичных папок**

Microsoft Exchange Server позволяет пользователям создавать публичные папки и размещать в них сообщения. Чтобы сделать это через ваше приложение, используйте класс Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), чтобы подключиться к серверу Exchange и читать и загружать сообщения и посты из публичных папок. Следующий фрагмент кода показывает, как прочитать все публичные папки и подпапки, а также перечислить и загрузить любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, так как только они поддерживают EWS.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
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
        Console.WriteLine("Имя: " + publicFolder.DisplayName);
        Console.WriteLine("Количество подпапок: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);
    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Имя папки: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir +  msg.Subject + ".msg",  SaveOptions.DefaultMsgUnicode);
    }

    // Вызывайте этот метод рекурсивно для любых подпапок
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

Вы можете перемещать электронные сообщения из одной папки в другую с помощью метода [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/) интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Он принимает параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI папки назначения.
  
### **Перемещение сообщений между папками**

Следующий фрагмент кода показывает, как переместить сообщение в почтовом ящике из папки «Входящие» в папку под названием «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
2. Обрабатывает некоторые сообщения на основе определенных критериев (в этом примере мы ищем ключевое слово в теме сообщения).
3. Перемещает сообщения, которые выполняют данное условие, в папку обработанных.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Перечислить все сообщения из папки «Входящие»
Console.WriteLine("Перечисление всех сообщений из «Входящих»....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Переместить сообщение в папку «Обработано» после обработки определенных сообщений на основе некоторых критериев
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("обработать это сообщение") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Сообщение перемещено...." + msgInfo.Subject);
    }
    else
    {
        // Сделать что-то еще
    }
}
```

## **Удаление сообщений**

Вы можете удалить электронные сообщения из папки с помощью метода [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) класса [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/). Он принимает уникальный URI сообщения в качестве параметра.

Следующий фрагмент кода показывает, как удалить сообщение из папки «Входящие». Для этой цели код:

1. Читает сообщения из папки «Входящие».
2. Обрабатывает сообщения на основе определенных критериев (в этом примере мы ищем ключевое слово в теме сообщения).
3. Удаляет сообщение.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Перечислить все сообщения из папки «Входящие»
Console.WriteLine("Перечисление всех сообщений из «Входящих»....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Удалить сообщение на основе некоторых критериев
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("удалить") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Сообщение удалено...." + msgInfo.Subject);
    }
    else
    {
        // Сделать что-то еще
    }
}
```

## **Копирование сообщений**

API Aspose.Email позволяет копировать сообщение из одной папки в другую с помощью метода [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/). Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.

### **Копирование сообщения в другую папку**

Следующий фрагмент кода показывает, как скопировать сообщение в другую папку.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Создать экземпляр класса EWSClient, указав учетные данные
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Копирование сообщения и получение ссылки на новый элемент копии");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```