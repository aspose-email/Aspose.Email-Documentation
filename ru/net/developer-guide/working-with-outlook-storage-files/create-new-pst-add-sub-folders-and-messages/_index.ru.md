---
title: "Создание нового PST, добавление подпапок и сообщений"
url: /ru/net/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Кроме разбора существующего PST файла, Aspose.Email предоставляет возможность создать PST файл с нуля. Эта статья демонстрирует, как создать файл PST для Outlook и добавить к нему подпапку.

1. [Создание нового PST файла](#creating-a-new-pst-file).
1. [Изменение класса контейнера папки](#changing-a-folders-container-class).
1. [Добавление массовых сообщений с улучшенной производительностью](#add-bulk-messages-with-improved-performance) 

## **Создание нового PST файла**

Используйте класс [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) для создания PST файла в каком-либо месте на локальном диске. Чтобы создать PST файл с нуля:

1. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
1. Добавьте подпапку в корень PST файла, получив доступ к корневой папке, а затем вызвав метод [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/). 

Следующий фрагмент кода показывает, как создать PST файл и добавить подпапку с названием Входящие.

```csharp
// Создание нового PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Добавление новой папки "Тест"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Проверка соответствия класса контейнера при добавлении папки в PST**

При создании новых папок или добавлении элементов в существующие папки важно убедиться, что класс контейнера нового элемента или папки совпадает с классом контейнера родительской папки, чтобы поддерживать организационную иерархию внутри PST файла. Для этой цели в Aspose.Email есть свойство [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) класса [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class). Это свойство указывает, следует ли проверять класс контейнера добавляемой папки по сравнению с классом контейнера родительской папки. Если установлено 'true', то будет выброшено исключение, если классы контейнеров не совпадают. По умолчанию 'false'.

Следующий фрагмент кода демонстрирует использование свойства [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) для управления тем, должно ли быть выброшено исключение при добавлении папок с несовпадающими классами контейнеров: 

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Создание стандартной папки Контакты с классом контейнера IPF.Contacts.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    
    // Исключение не произойдёт. EnforceContainerClassMatching по умолчанию равно false.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
    
    // Исключение произойдёт, поскольку класс контейнера добавляемой подпапки (IPF.Note) 
    // не совпадает с классом контейнера родительской папки (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Примечание: Обеспечьте правильную обработку исключений при принудительном соответствии классов контейнера, чтобы избежать неожиданного поведения при создании папок в PST.

## **Изменение класса контейнера папки**

Иногда необходимо изменить класс контейнера папки. Общий пример - это добавление сообщений разных типов (встреч, сообщений и т.д.) в одну папку. В таких случаях необходимо изменить класс папки для правильного отображения всех элементов в папке. Следующий фрагмент кода показывает, как изменить класс контейнера папки в PST для этой цели.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst");
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Добавление массовых сообщений с улучшенной производительностью**

Добавление отдельных сообщений в PST предполагает больше операций ввода-вывода с диском и может замедлить производительность. Чтобы улучшить производительность, сообщения можно добавить в PST в массовом режиме, чтобы минимизировать операции ввода-вывода.
Метод [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) позволяет добавлять сообщения оптом и может использоваться в следующих сценариях. Кроме того, событие [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) возникает, когда сообщение добавляется в папку.

### **Добавление сообщений из другого PST**

Чтобы добавить сообщения из другого PST, используйте метод [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/), который возвращает `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Получение папки по имени
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());


// Обработка события MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Добавлено: {e.EntryId}");
}
```

### **Добавление сообщений из директории**

Чтобы добавить сообщения из директории, создайте именованный итератор `GetMessages(string pathToDir)`, который возвращает `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Именованный итератор для чтения сообщений из директории.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Обработка события MessageAdded.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Добавлено: {e.EntryId}");
}
```