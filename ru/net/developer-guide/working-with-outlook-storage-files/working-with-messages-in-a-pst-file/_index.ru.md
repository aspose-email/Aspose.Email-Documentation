---
title: "Работа с сообщениями в PST-файле"
url: /ru/net/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---

## **Добавление сообщений в PST файлы**

Статья [Создание нового PST файла и добавление подкаталогов](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolderss) показывает, как создать PST файл и добавить подкаталог в него. С помощью Aspose.Email вы можете добавлять сообщения в подкаталоги PST файла, который вы создали или загрузили. Эта статья добавляет два сообщения с диска в подкаталог "Входящие" PST. Используйте классы [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) для добавления сообщений в PST файлы. Чтобы добавить сообщения в папку "Входящие" PST файла:

1. Создайте экземпляр класса FolderInfo и загрузите его с содержимым папки "Входящие".
2. Добавьте сообщения с диска в папку "Входящие", вызвав метод [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage). Класс [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) предоставляет метод [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages), который позволяет добавить большое количество сообщений в папку, уменьшая операции ввода-вывода на диск и повышая производительность. Полный пример можно найти ниже в разделе [Добавление массовых сообщений](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-bulk-messages).

Ниже приведен код, показывающий, как добавить сообщения в подкаталог PST с именем "Входящие".

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Создать новый PST            
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Добавьте новую папку "Входящие"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Выберите папку "Входящие"
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Добавьте несколько сообщений в папку "Входящие"
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Добавление массовых сообщений**

Добавление отдельных сообщений в PST предполагает больше операций ввода/вывода на диск и, следовательно, может замедлить производительность. Чтобы улучшить производительность, используйте метод AddMessages(IEnumerable<MapiMessage> messages) вместо метода AddMessage(MapiMessage message), чтобы минимизировать I/O операции. Кроме того, событие MessageAdded происходит, когда сообщение добавляется в папку.

### **Загрузка сообщений с диска**

Следующий фрагмент кода показывает, как загружать сообщения с диска.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
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

### **Реализация IEnumerable**

Следующий фрагмент кода показывает, как можно использовать реализацию IEnumerable.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
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

### **Добавление сообщений из другого PST**

Чтобы добавить сообщения из другого PST, используйте метод [FolderInfo.EnumerateMapiMessages()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/#enumeratemapimessages), который возвращает IEnumerable<MapiMessage>. Следующий фрагмент кода показывает, как добавить сообщения из другого PST.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Получите папку по имени
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Получите папку по имени
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }
}

/// <summary>
/// Обрабатывает событие MessageAdded.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Получение информации о сообщениях из Outlook PST файла**

В статье [Чтение Outlook PST файла и получение информации о папках и подкаталогах](https://docs.aspose.com/email/ru/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/) мы обсуждали, как загрузить PST файл Outlook и просматривать его папки для получения имен папок и количества сообщений в них. Эта статья объясняет, как прочитать все папки и подкаталоги в PST файле и отобразить информацию о сообщениях, например, тему, отправителя и получателей. PST файл Outlook может содержать вложенные папки. Чтобы получить информацию о сообщениях из них, а также из папок на верхнем уровне, используйте рекурсивный метод для чтения всех папок. Следующий фрагмент кода показывает, как прочитать PST файл Outlook и рекурсивно отобразить содержимое папок и сообщений.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Загрузите файл Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
       
        // Загрузите PST файл Outlook
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Получите формат отображения PST файла
        Console.WriteLine("Формат отображения: " + personalStorage.Format);

        // Получите информацию о папках и сообщениях
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Вызовите рекурсивный метод для отображения содержимого папки
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);               
    }            
}

/// <summary>
/// Это рекурсивный метод для отображения содержимого папки
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Отобразите имя папки
    Console.WriteLine("Папка: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Отобразите информацию о сообщениях внутри этой папки
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Тема: " + messageInfo.Subject);
        Console.WriteLine("Отправитель: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Получатели: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Вызовите этот метод рекурсивно для каждой подкласса
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Извлечение сообщений из PST файлов**

Эта статья показывает, как читать PST файлы Microsoft Outlook и извлекать сообщения. Сообщения затем сохраняются на диск в формате MSG.

{{% alert %}}
**Попробуйте!**

Запустите простой проект приложения [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) и изучите интересное использование возможностей Aspose.Email для чтения электронной почты из PST и поиска разговорных потоков.
{{% /alert %}}

Следующий фрагмент кода показывает, как извлекать сообщения из PST файла: 
- Используйте рекурсивный метод для просмотра всех папок (включая любые вложенные папки) и вызова метода PersonalStorage.ExtractMessage() для получения сообщений Outlook в экземпляр класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). 
- После этого вызовите метод MapiMessage.Save() для сохранения сообщения либо на диск, либо в поток в формате MSG.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // Путь к директории файлов.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Загрузите файл Outlook
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // загрузите PST файл Outlook
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // получите формат отображения PST файла
        Console.WriteLine("Формат отображения: " + pst.Format);

        // получите информацию о папках и сообщениях
        FolderInfo folderInfo = pst.RootFolder;

        // Вызовите рекурсивный метод для извлечения msg файлов из каждой папки
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }            
}

/// <summary>
/// Это рекурсивный метод для отображения содержимого папки
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // отобразите имя папки
    Console.WriteLine("Папка: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // пройдитесь по всем сообщениям в этой папке
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Сохранение сообщения {0} ....", messageInfo.Subject);
        // получите сообщение в экземпляре MapiMessage
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // сохраните это сообщение на диск в формате msg
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // сохраните это сообщение в поток в формате msg
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Вызовите этот метод рекурсивно для каждой подкаталог
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Сохранение сообщений непосредственно из PST в поток**

Чтобы сохранить сообщения из PST файла непосредственно в поток, не извлекая MsgInfo для сообщений, используйте метод SaveMessageToStream(). Следующий фрагмент кода показывает, как сохранить сообщения непосредственно из PST в поток.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
string dataDir = RunExamples.GetDataDir_Outlook();

// Загрузите файл Outlook
string path = dataDir + "PersonalStorage.pst";

// Сохранить сообщение в MemoryStream
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

// Сохранить сообщение в файл
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
    
    // Для перечисления entryId сообщений вы можете использовать метод FolderInfo.EnumerateMessagesEntryId():
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}            
```

### **Извлечение n числа сообщений из PST файла**

Следующий фрагмент кода показывает, как извлечь определенное количество сообщений из PST. Просто укажите индекс для первого сообщения и общее количество сообщений для извлечения.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Извлечение сообщений, начиная с 10 индекса сверху и извлечение в целом 100 сообщений
MessageInfoCollection messages = inbox.GetContents(10, 100);
```
### **Получение общего количества элементов из PST файла**

Aspose.Email предоставляет метод [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) свойства [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property). Он возвращает общее количество элементов сообщения, содержащихся в PST.

Следующий код показывает, как получить общее количество элементов (сообщений, назначений, контактов и т.д.), хранящихся в PST файле:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

## **Удаление элементов из PST файлов**

Статья [Добавление сообщений в PST файлы](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-messages-to-pst-files) показывает, как добавлять сообщения в PST файлы. Также, конечно, возможно удалить элементы (содержимое) из PST файла и может быть желаемо удалить сообщения в массовом порядке. Элементы из PST файла можно удалить, используя метод [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem). API также предоставляет метод [FolderInfo.DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) для массового удаления элементов из PST файла.

### **Удаление сообщений из PST файлов**

Эта статья показывает, как использовать класс [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) для доступа к конкретным папкам в PST файле. Чтобы удалить сообщения из подкаталога "Отправленные" ранее загруженного или созданного PST файла:

1. Создайте экземпляр класса [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) и загрузите его с содержимым подкаталога "Отправленные".
1. Удалите сообщения из папки "Отправленные", вызвав метод [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) и передав [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) в качестве параметра. Следующий фрагмент кода показывает, как удалять сообщения из подкаталога "Отправленные" PST файла.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Загрузите PST файл Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Получите папку отправленных элементов
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("некоторое условие удаления") == true)
    {
        // Удалите этот элемент
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Удалено это сообщение");
    }
}
```

### **Удаление папок из PST файлов**

Вы можете удалить папку PST, переместив ее в папку "Удаленные элементы".

```csharp
using (PersonalStorage pst = PersonalStorage.FromFile(@"test.pst"))
{
    FolderInfo deletedItemsFolder = pst.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.RootFolder.GetSubFolder("Пустая папка");
	  FolderInfo someFolder = pst.RootFolder.GetSubFolder("Некоторая папка");
    pst.MoveItem(emptyFolder, deletedItemsFolder);
	  pst.MoveItem(someFolder, deletedItemsFolder);
}
```

Преимущество этого метода заключается в том, что удаленная папка может быть легко восстановлена.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Некоторая папка");
pst.MoveItem(someFolder, pst.RootFolder);
```

Вы также можете навсегда удалить папку из папки "Удаленные элементы", если это необходимо.

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

Метод [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) может использоваться для любых папок, если вы хотите немедленно и навсегда удалить подпапку, минуя папку "Удаленные элементы".

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Некоторая папка");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```
### **Удаление элементов из PST**

Удалите элементы (папки или сообщения) из таблицы личного хранения (PST), используя уникальный entryId, связанный с элементом, вызвав метод DeleteItem(string entryId) класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).

Следующий фрагмент кода можно использовать для вызова метода DeleteItem и передачи entryId в качестве параметра:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```
**Обратите внимание:**

- Этот метод навсегда удалит элемент из PST, и это действие не может быть отменено. Будьте осторожны при использовании этого метода, чтобы избежать случайной потери данных.
- Согласно стандартным соглашениям, убедитесь, что entryId действителен и соответствует существующему элементу в PST. 
- В противном случае будет выдано исключение. Рекомендуется иметь резервную копию PST или реализовать соответствующие меры для восстановления удаленных элементов при необходимости.

### **Массовое удаление элементов из PST файла**

API Aspose.Email может использоваться для массового удаления элементов из PST файла. Это достигается с помощью метода [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems), который принимает список идентификаторов элементов, относящихся к элементам, которые нужно удалить. Следующий фрагмент кода показывает, как удалять элементы массово из PST файла.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Получите подкаталог "Входящие" из файла Outlook
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Создайте экземпляр PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // удалите сообщения с From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Поиск сообщений и папок в PST по критериям**

Файлы личного хранения (PST) могут содержать огромное количество данных. Поиск данных, соответствующих определенному критерию в таких больших файлах, требует включения нескольких контрольных точек в код для фильтрации информации. С помощью класса [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) Aspose.Email позволяет искать конкретные записи в PST на основе заданного критерия поиска. PST может быть отсканирован на наличие сообщений на основе параметров поиска, таких как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. Класс [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) также может использоваться для поиска подкаталогов.

### **Поиск сообщений и папок в PST**

Следующий фрагмент кода показывает, как использовать класс [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) для поиска содержимого в PST на основе различных критериев поиска. Например, он показывает поиск PST на основе:

- Важности сообщения.
- Класса сообщения.
- Наличие вложений.
- Размер сообщения.
- Непрочитанных сообщений.
- Непрочитанных сообщений с вложениями и
- папок с конкретным именем подкаталога.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // Сообщения высокой важности
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Сообщения с высокой важностью:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Сообщения с IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Сообщения с вложениями И высокой важностью
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Сообщения с вложениями: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Сообщения размером > 15 КБ
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("сообщения размером > 15 Кб:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Непрочитанные сообщения
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Непрочитанные:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Непрочитанные сообщения с вложениями
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Непрочитанные сообщения с вложениями: " + messages.Count);

    // Папка с именем 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Папка, имеющая подкаталог: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Папки с подкаталогами
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```

### **Поиск строки в PST с параметром игнорирования регистра**

Следующий фрагмент кода показывает, как искать строку в PST с параметром игнорирования регистра.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase равно True
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

### **Поиск тем сообщений по нескольким ключевым словам в PST файле**

Вы можете использовать метод [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) для поиска сообщений с темой, содержащей хотя бы одно из указанных слов, как показано ниже:

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET

var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' это ключевое слово для поиска

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' также ключевое слово для поиска

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // темы сообщений должны содержать слова 'Review' или 'Error'

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

## **Перемещение элементов в другие папки PST файла**

Aspose.Email позволяет перемещать элементы из исходной папки в другую папку в одном и том же файле личного хранения (PST). Это включает в себя:

- Перемещение определенной папки в новую родительскую папку.
- Перемещение определенных сообщений в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подкаталогов в новую родительскую папку.

Следующий фрагмент кода показывает, как перемещать элементы, такие как сообщения и папки, из исходной папки в другую папку в одном и том же PST файле.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Переместить папку и сообщение в папку "Удаленные элементы"
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Переместить все подпапки "Входящие" и содержимое подкаталога в папку "Удаленные элементы"
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```
## **Слияние и разделение PST файлов**

Пример кода ниже описывает процесс разделения файла:

1. Сначала он использует метод [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class), чтобы указать имя файла.

2. Затем он вызывает делегат [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) для обработки события StorageProcessed.

3. Класс [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingevenargs/) предоставляет данные для события PersonalStorage.StorageProcessing. Его свойство [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventargs/filename/#storageprocessedeventargsfilename-property) позволяет вам получить имя PST файла. Для метода [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) это будет имя текущего PST, который будет объединен с основным, а для метода [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) это будет имя текущей части.

4. Наконец, перегруженный метод [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) запустит процесс разделения PST хранилища на более мелкие части. Он принимает следующие параметры:

- **chunkSize**: Приблизительный размер каждого фрагмента в байтах.
- **partFileNamePrefix**: Префикс, который будет добавлен к имени файла каждой части PST. Если предоставлен, префикс будет добавлен в начало каждого имени файла. Если не предоставлен (null или пустой), части PST будут созданы без префикса.
- **path**: Путь к папке, где будут созданы куски.

Имя файла каждой части следует шаблону: {prefix}part{number}.pst, где {prefix} представляет префикс имени файла (если предоставлен), а {number} представляет номер фрагмента файла.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Событие обработки хранилища было вызвано для файла: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

## **Обновление свойств сообщений в PST файле**

Иногда требуется обновить определенные свойства сообщений, такие как изменение темы, пометка важности сообщения и аналогичные другие. Обновление сообщения в PST файле с такими изменениями в свойствах сообщения может быть достигнуто с помощью метода [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/). Эта статья показывает, как обновить сообщения массово в PST файле для изменения свойств. Следующий фрагмент кода показывает, как обновить свойства сообщений в массовом режиме для нескольких сообщений в PST файле.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Загрузите PST файл Outlook
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
            
// Получите необходимую подкатегорию 
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// найдите сообщения с From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Получите содержимое из запроса
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Сохраните (MessageInfo,EntryIdString) в списке
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Составьте новые свойства
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("Новая тема")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// обновить сообщения с From = "someuser@domain.com" новыми свойствами
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Обновление пользовательских свойств в PST файле**

Иногда требуется пометить элементы, которые были обработаны в PST файле. API Aspose.Email позволяет достичь этого с помощью MapiProperty и MapiNamedProperty. Следующие методы полезны в достижении этого.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- FolderInfo.ChangeMessages(MapiPropertyCollection updatedProperties) - изменяет все сообщения в папке
- PersonalStorage.ChangeMessage(string entryId, MapiPropertyCollection updatedProperties) - изменяет свойства сообщения

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Загрузите файл Outlook
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Создайте коллекцию свойств сообщения для добавления или обновления
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Обычное, Пользовательское и PidLidLogFlags именованное свойство
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

API Aspose.Email может использоваться для извлечения вложений из сообщений PST без предварительного извлечения полного сообщения. Метод ExtractAttachments класса IEWSClient может быть использован для этого. Следующий фрагмент кода показывает, как извлечь вложения без извлечения полного сообщения.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
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

Ключевая функциональность Microsoft Outlook состоит в управлении электронной почтой, календарями, задачами, контактами и записями журнала. Кроме того, в папку PST можно также добавлять файлы, и полученный PST будет вести учет добавленных документов. Aspose.Email предоставляет возможность добавления файлов в папку так же, как и добавление сообщений, контактов, задач и записей журнала в PST. Следующий фрагмент кода показывает, как добавлять документы в папку PST с помощью Aspose.Email.

```csharp
// Для полных примеров и файлов данных посетите https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Добавить файл Document.doc с классом сообщения "IPM.Document" по умолчанию.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```