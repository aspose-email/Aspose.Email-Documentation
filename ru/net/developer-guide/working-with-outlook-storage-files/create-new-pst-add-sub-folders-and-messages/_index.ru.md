---
title: "Создайте новый PST, добавьте подпапки и сообщения"
url: /ru/net/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Помимо анализа существующего файла PST, Aspose.Email предоставляет средства для создания файла PST с нуля. В этой статье показано, как создать файл Outlook PST и добавить в него подпапку.

1. [Создание нового файла PST](#creating-a-new-pst-file).
1. [Изменение класса Container папки](#changing-a-folders-container-class).
1. [Добавляйте массовые сообщения с улучшенной производительностью](#add-bulk-messages-with-improved-performance)

## **Создайте новый файл PST**

Используйте [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) класс для создания файла PST в каком-то месте на локальном диске. Чтобы создать файл PST с нуля, выполните следующие действия:

1. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
1. Добавьте подпапку в корень файла PST, открыв корневую папку и вызвав [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/) method.

В следующем фрагменте кода показано, как создать файл PST и добавить подпапку под названием «Входящие».

```csharp
// Create new PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Add new folder "Test"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Проверка соответствия классов контейнеров при добавлении папки в PST**

При создании новых папок или добавлении элементов в существующие папки важно обеспечить соответствие класса контейнера нового элемента или папки классу контейнера родительской папки для сохранения организационной иерархии в файле хранилища PST. Для этого в Aspose.Email есть [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) собственность [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) класс. Свойство указывает, следует ли принудительно сравнивать класс контейнера добавляемой папки с классом контейнера родительской папки. Если задано значение «true», в случае несовпадения классов контейнеров будет создано исключение. По умолчанию установлено значение «false».

Следующий пример кода демонстрирует использование [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) свойство, определяющее, следует ли создавать исключение при добавлении папок с несовпадающими классами контейнеров:

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Create a standard Contacts folder with the IPF.Contacts container class.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
   
    // An exception will not arise. EnforceContainerClassMatching is false by default.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
   
    // An exception will occur as the container class of the subfolder being added (IPF.Note)
    // does not match the container class of the parent folder (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Примечание. Обеспечьте надлежащую обработку исключений при принудительном сопоставлении классов контейнеров, чтобы предотвратить непредвиденное поведение при создании папки в PST.

## **Изменение класса контейнера папок**

Иногда необходимо изменить класс контейнера папок. Типичный пример: сообщения разных типов (встречи, сообщения и т. д.) добавляются в одну и ту же папку. В таких случаях класс папки необходимо изменить, чтобы все элементы в папке отображались корректно. В следующем фрагменте кода показано, как изменить класс контейнера папки в PST для этой цели.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst);
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Добавляйте массовые сообщения с улучшенной производительностью**

Добавление отдельных сообщений в PST подразумевает большее количество операций ввода-вывода на диск и может замедлить производительность. Для повышения производительности сообщения можно добавлять в PST в массовом режиме, чтобы свести к минимуму количество операций ввода-вывода. [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) Метод позволяет массово добавлять сообщения и может использоваться в следующих сценариях. Кроме того, [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) событие происходит при добавлении сообщения в папку.

### **Добавить сообщения из другого PST**

Чтобы добавить сообщения из другого PST, используйте [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) метод, который возвращает `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Get the folder by name
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());


// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

### **Добавить сообщения из каталога**

Чтобы добавить сообщения из каталога, создайте `GetMessages(string pathToDir)` именованный метод итератора, который возвращает `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Named iterator method to read messages from directory.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

