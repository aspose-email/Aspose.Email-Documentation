---
title: "Работа с сообщениями в файле PST"
url: /ru/net/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---


## **Добавление сообщений в файлы PST**

The [Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolderss) В статье показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавлять сообщения в подпапки созданного или загруженного файла PST. В этой статье два сообщения с диска добавляются во вложенную папку «Входящие» PST. Используйте [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) классы для добавления сообщений в файлы PST. Чтобы добавить сообщения в папку «Входящие» PST-файла, выполните следующие действия:

1. Создайте экземпляр класса FolderInfo и загрузите в него содержимое папки «Входящие».
2. Добавьте сообщения с диска в папку «Входящие», вызвав [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage) метод. [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) класс раскрывает [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages) метод, позволяющий добавлять большое количество сообщений в папку, сокращая количество операций ввода-вывода на диск и повышая производительность. Полный пример можно найти ниже, в [Добавление массовых сообщений](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-bulk-messages).

В приведенном ниже фрагменте кода показано, как добавлять сообщения в подпапку PST под названием «Входящие».

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create new PST           
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Добавление массовых сообщений**

Добавление отдельных сообщений в PST подразумевает большее количество операций ввода-вывода на диск и, следовательно, может снизить производительность. Чтобы повысить производительность, используйте AddMessages (IEnumerable)<MapiMessage> messages) вместо метода addMessage (сообщение MapiMessage) для минимизации операций ввода-вывода. Кроме того, событие MessageAdded возникает при добавлении сообщения в папку.

### **Загрузка сообщений с диска**

В следующем фрагменте кода показано, как загружать сообщения с диска.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void AddMessagesInBulkMode(string fileName, string msgFolderName)
{
    using (PersonalStorage personalStorage = PersonalStorage.FromFile(fileName))
    {
        FolderInfo folder = personalStorage.RootFolder.GetSubFolder("myInbox");
        folder.MessageAdded += OnMessageAdded;
        folder.AddMessages(new MapiMessageCollection(msgFolderName));
    }
}
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

### **Неисчислимая реализация**

В следующем фрагменте кода показано, как можно использовать реализацию IEnumerable.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public class MapiMessageCollection : IEnumerable<MapiMessage>
{
    private string path;

    public MapiMessageCollection(string path)
    {
        this.path = path;
    }

    public IEnumerator<MapiMessage> GetEnumerator()
    {
        return new MapiMessageEnumerator(path);
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}

public class MapiMessageEnumerator : IEnumerator<MapiMessage>
{
    private readonly string[] files;

    private int position = -1;

    public MapiMessageEnumerator(string path)
    {
        string path1 = RunExamples.GetDataDir_Outlook();
        files = Directory.GetFiles(path1);
    }

    public bool MoveNext()
    {
        position++;
        return (position < files.Length);
    }

    public void Reset()
    {
        position = -1;
    }

    object IEnumerator.Current
    {
        get
        {
            return Current;
        }
    }

    public MapiMessage Current
    {
        get
        {
            try
            {
                return MapiMessage.FromFile(files[position]);
            }
            catch (IndexOutOfRangeException)
            {
                throw new InvalidOperationException();
            }
        }
    }
    public void Dispose()
    {
    }
}
```

### **Добавление сообщений из других PST**

Чтобы добавить сообщения из другого PST, используйте [FolderInfo.EnumerateMapiMessages()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/#enumeratemapimessages) метод, возвращающий IEnumerable<MapiMessage>. В следующем фрагменте кода показано, как добавлять сообщения из другого PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Get the folder by name
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Get the folder by name
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }

}

/// <summary>
/// Handles the MessageAdded event.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Получение информации о сообщениях из файла Outlook PST**

In [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](https://docs.aspose.com/email/ru/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/) в статье мы обсуждали, как загрузить файл Outlook PST и просмотреть его папки, чтобы узнать имена папок и количество сообщений в них. В этой статье объясняется, как читать все папки и подпапки в файле PST и отображать информацию о сообщениях, например тему, отправителя и получателя. Файл Outlook PST может содержать вложенные папки. Чтобы получить информацию о сообщениях из этих папок, а также из папок верхнего уровня, используйте рекурсивный метод чтения всех папок. В следующем фрагменте кода показано, как читать PST-файл Outlook и рекурсивно отображать содержимое папки и сообщения.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{           
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
      
        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Get the Display Format of the PST file
        Console.WriteLine("Display Format: " + personalStorage.Format);

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Call the recursive method to display the folder contents
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);              
    }           
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Subject: " + messageInfo.Subject);
        Console.WriteLine("Sender: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Recipients: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Извлечение сообщений из файлов PST**

В этой статье показано, как читать файлы Microsoft Outlook PST и извлекать сообщения. Затем сообщения сохраняются на диск в формате MSG.

{{% alert %}}
**Попробуйте!**

Запустите [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) простой проект приложения и изучите интересное использование функций Aspose.Email для чтения писем из PST и поиска тем разговоров.
{{% /alert %}}

В следующем фрагменте кода показано, как извлекать сообщения из файла PST:
- Используйте рекурсивный метод для просмотра всех папок (включая любые вложенные папки) и вызовите метод PersonalStorage.extractMessage (), чтобы поместить сообщения Outlook в экземпляр [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class.
- После этого вызовите метод MapiMessage.save (), чтобы сохранить сообщение на диске или в потоке в формате MSG.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{           
    // The path to the file directory.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // get the Display Format of the PST file
        Console.WriteLine("Display Format: " + pst.Format);

        // get the folders and messages information
        FolderInfo folderInfo = pst.RootFolder;

        // Call the recursive method to extract msg files from each folder
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }           
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Saving message {0} ....", messageInfo.Subject);
        // get the message in MapiMessage instance
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // save this message to disk in msg format
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // save this message to stream in msg format
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Сохранение сообщений непосредственно из PST в потоковую передачу**

Чтобы сохранить сообщения из файла PST непосредственно в поток, не извлекая MsgInfo для сообщений, используйте метод SaveMessageToStream (). В следующем фрагменте кода показано, как сохранять сообщения непосредственно из PST в поток.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the file directory.
string dataDir = RunExamples.GetDataDir_Outlook();

// Load the Outlook file
string path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
using (PersonalStorage personalStorage = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (MemoryStream memeorystream = new MemoryStream())
        {
            personalStorage.SaveMessageToStream(messageInfo.EntryIdString, memeorystream);
        }
    }
}

// Save message to file
using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (FileStream fs = File.OpenWrite(messageInfo.Subject + ".msg"))
        {
            pst.SaveMessageToStream(messageInfo.EntryIdString, fs);
        }
    }
}

using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
   
    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}           
```

### **Извлечение n количества сообщений из PST-файла**

В следующем фрагменте кода показано, как извлечь заданное количество сообщений из PST. Просто укажите индекс первого сообщения и общее количество сообщений, которые нужно извлечь.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.GetContents(10, 100);
```
### **Получение общего количества элементов из файла PST**

Aspose.Email предоставляет [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) метод [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property) имущество. Оно возвращает общее количество сообщений, содержащихся в PST.

В следующем примере кода показано, как получить общее количество элементов (сообщений, встреч, контактов и т. д.), хранящихся в файле PST:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

## **Удалить элементы из файлов PST**

The [Добавление сообщений в файлы PST](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-messages-to-pst-files) в статье показано, как добавлять сообщения в файлы PST. Конечно, также можно удалять элементы (содержимое) из файла PST, и может быть желательно удалять сообщения массово. Элементы из файла PST можно удалить с помощью [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) метод. API также предоставляет [FolderInfo.DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) метод массового удаления элементов из файла PST.

### **Удаление сообщений из PST-файлов**

В этой статье показано, как использовать [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) класс для доступа к определенным папкам в файле PST. Чтобы удалить сообщения из подпапки «Отправленные» ранее загруженного или созданного файла PST, выполните следующие действия:

1. Создайте экземпляр [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) класс и загрузите его вместе с содержимым отправленной подпапки.
1. Удалите сообщения из папки «Отправленные», вызвав [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) метод и передача [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) в качестве параметра. В следующем фрагменте кода показано, как удалять сообщения из вложенной папки Sent PST-файла.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("some delete condition") == true)
    {
        // Delete this item
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Deleted this message");
    }
}
```

### **Удаление папок из файлов PST**

Папку PST можно удалить, переместив ее в папку «Удаленные».

```csharp
using (PersonalStorage pst = PersonalStorage.FromFile(@"test.pst"))
{
    FolderInfo deletedItemsFolder = pst.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.RootFolder.GetSubFolder("Empty folder");
	  FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
    pst.MoveItem(emptyFolder, deletedItemsFolder);
	  pst.MoveItem(someFolder, deletedItemsFolder);
}
```

Преимущество этого метода в том, что удаленную папку можно легко восстановить.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Some folder");
pst.MoveItem(someFolder, pst.RootFolder);
```

При необходимости можно также навсегда удалить папку из папки «Удаленные».

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

The [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) метод можно использовать для любых папок, если вы хотите немедленно и навсегда удалить подпапку, минуя папку «Удаленные элементы».

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```
### **Удалить элементы из PST**

Удалите элементы (папки или сообщения) из таблицы личного хранилища (PST), используя уникальный идентификатор записи, связанный с элементом, вызвав метод DeleteItem (строка entryID) [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.

Следующий фрагмент кода можно использовать для вызова метода DeleteItem и передачи EntryId в качестве параметра:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```
**Обратите внимание:**

- Этот метод безвозвратно удалит элемент из PST и не может быть отменен. При использовании этого метода соблюдайте осторожность, чтобы избежать случайной потери данных.
- В соответствии со стандартными соглашениями убедитесь, что EntryID действителен и соответствует существующему элементу в PST.
- В противном случае будет создано исключение. Рекомендуется создать резервную копию файла PST или при необходимости принять соответствующие меры для восстановления удаленных элементов.

### **Массовое удаление элементов из файла PST**

Aspose.Email API можно использовать для массового удаления элементов из файла PST. Это достигается с помощью [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems) метод, который принимает список элементов Entry ID, относящихся к удаляемым элементам. В следующем фрагменте кода показано, как массово удалять элементы из файла PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // delete messages having From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Поиск сообщений и папок в PST по критерию**

Файлы персонального хранилища (PST) могут содержать огромное количество данных. При поиске данных, отвечающих определенным критериям в таких больших файлах, необходимо включить в код несколько контрольных точек для фильтрации информации. С помощью [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) class, Aspose.Email позволяет искать определенные записи в PST на основе заданных критериев поиска. В PST можно искать сообщения на основе таких параметров поиска, как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) также можно использовать для поиска подпапок.

### **Поиск сообщений и папок в PST**

В следующем фрагменте кода показано, как использовать [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) класс для поиска содержимого в PST на основе различных критериев поиска. Например, он показывает поиск в PST на основе:

- Важность сообщения.
- Класс сообщений.
- Наличие вложений.
- Размер сообщения.
- Непрочитанные сообщения.
- Непрочитанные сообщения с вложениями и
- папки с определенным именем подпапки.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with High Imp:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with atts: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("messags size > 15Kb:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread msgs with atts: " + messages.Count);

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Folder having subfolder: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```

### **Поиск строки в PST с параметром Ignore Case**

В следующем фрагменте кода показано, как искать строку в PST с помощью параметра ignore case.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase is True
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

### **Поиск тем сообщений по нескольким ключевым словам в файле PST**

Вы можете использовать [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) метод поиска сообщений, тема которых содержит хотя бы одно из указанных слов, как показано ниже:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' is key word for the search

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' is also key word for the search

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // message subjects must contain 'Review' or 'Error' words

using (var storage = PersonalStorage.FromFile("example.pst"))
{
    var folderInfo = storage.RootFolder.GetSubFolder("Inbox");
    var messageInfos = folderInfo.GetContents(queryBuilder.GetQuery());

    foreach (var messageInfo in messageInfos)
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

## **Переместить элементы в другие папки файла PST**

Aspose.Email позволяет перемещать элементы из исходной папки в другую папку в том же файле личного хранилища (PST). Сюда входят:

- Перемещение указанной папки в новую родительскую папку.
- Перемещение указанных сообщений в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подпапок в новую родительскую папку.

В следующем фрагменте кода показано, как перемещать такие элементы, как сообщения и папки, из исходной папки в другую папку того же файла PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```
## **Объединение и разделение файлов PST**

В приведенном ниже примере кода описан процесс разделения файла:

1. Он, во-первых, использует [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) метод [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) класс для указания имени файла.

2. Затем оно называет [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) делегат для обработки события StorageProcessed.

3. The [StorageProcessingEventArgs]() класс предоставляет данные для события PersonalStorage.StorageProcessing. Это [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventargs/filename/#storageprocessedeventargsfilename-property) свойство позволяет получить имя файла PST. Для [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) метод это будет имя текущего поста, который нужно объединить с основным, а для [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) метод это будет имя текущей детали.

4. Finally, [Разделить на (размер длинного фрагмента, префикс имени файла строковой части, путь к строке)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) метод перегрузки запустит разделение хранилища PST на части меньшего размера. Он принимает следующие параметры:

- **chunkSize**: Приблизительный размер каждого фрагмента в байтах.
- **partFileNamePrefix**: Префикс, добавляемый к имени файла каждой части PST. Если указано, префикс будет добавлен в начало имени каждого файла. Если не указано иное (пусто или пусто), части PST будут созданы без префикса.
- **path**: Путь к папке, в которой будут созданы фрагменты.

Имя файла каждой части соответствует шаблону: {prefix} part {number} .pst, где {prefix} представляет собой префикс имени файла (если указан), а {number} представляет номер фрагмента файла.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Storage processing event raised for file: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

## **Обновление свойств сообщения в файле PST**

Иногда требуется обновить некоторые свойства сообщений, такие как смена темы, маркировка важности сообщения и т. д. Обновление сообщения в PST-файле с такими изменениями в свойствах сообщения можно осуществить с помощью [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/) метод. В этой статье показано, как массово обновлять сообщения в PST-файле для изменения свойств. В следующем фрагменте кода показано, как массово обновлять свойства сообщений для нескольких сообщений в PST-файле.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
           
// Get Requierd Subfolder
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Save (MessageInfo,EntryIdString) in List
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("New Subject")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Обновление настраиваемых свойств в файле PST**

Иногда требуется пометить элементы, обработанные в файле PST. API Aspose.Email позволяет сделать это с помощью свойств MapiProperty и MapInamedProperty. В этом помогают следующие методы.

- actor MapInamed Property (длинный тег свойства, идентификатор строкового имени, идентификатор свойства GUID, значение свойства byte [])
- actor MapInamed Property (длинный тег свойства, идентификатор длинного имени, идентификатор свойства GUID, значение свойства byte [])
- FolderInfo.changeMessages (обновленные свойства коллекции MAPIPropertyCollection) — изменяет все сообщения в папке
- PersonalStorage.change Message (идентификатор строковой записи, обновленные свойства коллекции свойств MAPI) — изменяет свойства сообщения

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Load the Outlook file
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Create the collection of message properties for adding or updating
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Normal,  Custom and PidLidLogFlags named  property
		MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W,Encoding.Unicode.GetBytes("test_address@org.com"));
		MapiProperty namedProperty1 = new MapiNamedProperty(GenerateNamedPropertyTag(0, MapiPropertyType.PT_LONG),"ITEM_ID",Guid.NewGuid(),BitConverter.GetBytes(123));
		MapiProperty namedProperty2 = new MapiNamedProperty(GenerateNamedPropertyTag(1, MapiPropertyType.PT_LONG),0x0000870C,new Guid("0006200A-0000-0000-C000-000000000046"),BitConverter.GetBytes(0));
		newProperties.Add(namedProperty1.Tag, namedProperty1);
		newProperties.Add(namedProperty2.Tag, namedProperty2);
		newProperties.Add(property.Tag, property);
		testFolder.ChangeMessages(testFolder.EnumerateMessagesEntryId(), newProperties);
	}
}

private static long GenerateNamedPropertyTag(long index, MapiPropertyType dataType)
{
	return (((0x8000 | index) << 16) | (long)dataType) & 0x00000000FFFFFFFF;
}
```

## **Извлечение вложений без извлечения полного сообщения**

Aspose.Email API можно использовать для извлечения вложений из сообщений PST без предварительного извлечения всего сообщения. Для этого можно использовать метод ExtractAttachments в IEWSClient. В следующем фрагменте кода показано, как извлекать вложения без извлечения целого сообщения.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalstorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalstorage.RootFolder.GetSubFolder("Inbox");

    foreach (var messageInfo in folder.EnumerateMessagesEntryId())
    {
        MapiAttachmentCollection attachments = personalstorage.ExtractAttachments(messageInfo);

        if (attachments.Count != 0)
        {
            foreach (var attachment in attachments)
            {
                if (!string.IsNullOrEmpty(attachment.LongFileName))
                {
                    if (attachment.LongFileName.Contains(".msg"))
                    {
                        continue;
                    }
                    else
                    {
                        attachment.Save(dataDir + @"\Attachments\" + attachment.LongFileName);
                    }
                }
            }
        }
    }
}
```

## **Добавление файлов в PST**

Ключевые функции Microsoft Outlook — управление электронной почтой, календарями, задачами, контактами и записями в журнале. Кроме того, файлы также можно добавлять в папку PST, и полученный PST сохраняет записи добавленных документов. Aspose.Email предоставляет возможность добавлять файлы в папку таким же образом, как и добавлять сообщения, контакты, задачи и журнальные записи в PST. В следующем фрагменте кода показано, как добавлять документы в папку PST с помощью Aspose.Email.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```
