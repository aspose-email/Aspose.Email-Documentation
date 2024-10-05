---
title: "Чтение файла OLM Outlook для Mac и получение информации о папках и подпапках"
url: /ru/net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM - это специфический формат файла, используемый Microsoft Outlook для хранения локальных данных, таких как электронные письма, вложения, заметки, данные календаря, контакты, задачи, история и многое другое. Файлы OLM совместимы только с Outlook для Mac и не могут быть открыты или доступны с помощью Outlook для Windows, который вместо этого использует формат файла PST.

## **Открытие файлов формата OLM**

Файлы формата OLM можно открыть двумя способами:

- с использованием конструктора
- с использованием статического метода FromFile

Существуют различия в поведении между этими методами. См. раздел ниже.

### **Открытие файлов с помощью конструктора**

Чтобы открыть файл, вызовите конструктор класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) и передайте полное имя файла или поток в качестве аргумента:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

### **Открытие файлов с использованием статического метода FromFile**

Чтобы открыть файл, используйте статический метод [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) и передайте полное имя файла или поток в качестве аргумента:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

## **Получение папок**

Чтобы получить доступ к структуре директорий файла OLM, создайте экземпляр класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) с использованием его конструктора и передайте путь к файлу.
После открытия файла получите доступ к его структуре директорий, используя свойство [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/). Это свойство возвращает список объектов [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/), каждый из которых представляет директорию в файле OLM.
Чтобы дальше исследовать структуру каталогов, получите доступ к свойству [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) каждого объекта, которое возвращает список его подпапок. Используя эти свойства, вы можете перемещаться по всей иерархии каталогов файла OLM и получать доступ ко всем директориям и подпапкам, которые он содержит.

Пример ниже отображает список всех папок в иерархическом порядке:

```cs
using (var olm = new OlmStorage(fileName))
{
    PrintAllFolders(olm.FolderHierarchy, string.Empty);
}

private void PrintAllFolders(List<OlmFolder> folderHierarchy, string indent)
{
    foreach (var folder in folderHierarchy)
    {
        Console.WriteLine($"{indent}{folder.Name}");
        PrintAllFolders(folder.SubFolders, indent+"-");
    }
}
```

При использовании метода [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) для открытия файла OLM свойство [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) по умолчанию не будет инициализировано и вернет null. В этом случае вызовите метод GetFolders явно, чтобы инициализировать свойство [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) и получить список директорий в файле OLM:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

Также можно получить любую папку по имени:

1. Вызовите метод [GetFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/getfolder/).
2. Передайте имя папки в качестве первого аргумента и значение, показывающее, следует ли игнорировать чувствительность к регистру при поиске папки, в качестве второго параметра.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // получить папку «Входящие» по имени
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

## **Список писем**

Класс [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/), представляющий папку, имеет следующие методы для получения списка писем:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) реализует итерацию по письмам в папке. В этом случае каждая итерация возвращает объект [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/), который предоставляет краткую информацию о письме.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), также реализует итерацию по письмам в папке, но в этом случае каждая итерация возвращает объект [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), представляющий само письмо, со всеми его свойствами.

### **Использование метода EnumerateMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);
    foreach (var messageInfo in folder.EnumerateMessages())
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

### **Использование метода EnumerateMapiMessages**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var msg in folder.EnumerateMapiMessages())
    {
        // сохранить сообщение в формате MSG
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Другие полезные свойства**

Другие полезные свойства класса OlmFolder включают: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) и [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) свойства, которые возвращают наличие сообщений в папке и их количество.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Количество сообщений: {folder.MessageCount}");
    }
}
```
### **Получение или установка даты изменения сообщения**

Дата изменения представляет собой дату и время последнего изменения сообщения OLM. Вы можете использовать свойство [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) для получения или обновления значения даты изменения сообщения OLM.

Вот пример, который демонстрирует использование этого свойства:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```
## **Извлечение писем**

Класс [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) имеет метод [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/), который позволяет извлекать письма. Этот метод принимает объект [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/).

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Извлеките сегодняшние сообщения из «Входящих»
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```
## **Извлечение всех элементов из письма с использованием Traversal API**

Вы можете извлечь все элементы из файла OLM Outlook, насколько это возможно, не вызывая исключений, даже если некоторые данные оригинального файла повреждены. Для этого используйте конструктор [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) и метод [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) вместо метода FromFile. Конструктор позволяет определить метод обратного вызова.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Код обработки исключений. */ }))
```
Метод обратного вызова делает доступными исключения загрузки и обхода.

Метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) возвращает 'true', если файл был успешно загружен и дальнейший обход возможен. Если файл поврежден и обход невозможен, возвращается 'false'.

```cs
if (olm.Load(fileName))
```

Следующий код-фрагмент и шаги показывают, как использовать этот API:

1. Создайте новый экземпляр класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), передав метод обратного вызова для обработки исключений, возникающих в процессе.
2. Загрузите файл OLM, вызвав метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) экземпляра OlmStorage. 
3. Если файл OLM успешно загружен, получите иерархию папок, вызвав метод [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) на экземпляре OlmStorage. Это возвращает список объектов OlmFolder.
4. Вызовите метод ExtractItems, передав экземпляр OlmStorage и список объектов OlmFolder.
5. В методе ExtractItems выполните итерацию по каждой папке в списке папок.
6. Если папка содержит сообщения (письма), выведите имя папки в консоль с помощью Console.WriteLine(folder).
7. Выполните итерацию по сообщениям текущей папки, вызвав метод EnumerateMessages на экземпляре OlmStorage, передав текущую папку в качестве аргумента.
8. Выведите тему каждого сообщения в консоль с помощью Console.WriteLine(msg.Subject).
9. Если папка имеет подпапки, рекурсивно снова вызовите метод ExtractItems, передав экземпляр OlmStorage и подпапки текущей папки.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Код обработки исключений. */ }))
{
    if (olm.Load(fileName))
    {
        var folderHierarchy = olm.GetFolders();
        ExtractItems(olm, folderHierarchy);
    }
}

private static void ExtractItems(OlmStorage olm, List<OlmFolder> folders)
{
    foreach (var folder in folders)
    {
        if (folder.HasMessages)
        {
            Console.WriteLine(folder);

            foreach (var msg in olm.EnumerateMessages(folder))
            {
                Console.WriteLine(msg.Subject);
            }
        }

        if (folder.SubFolders.Count > 0)
        {
            ExtractItems(olm, folder.SubFolders);
        }
    }
}
```
## **Извлечение сообщений из OLM по идентификаторам**

Процесс извлечения писем стал проще благодаря возможности извлекать выбранные сообщения OLM по идентификаторам. Это срочно необходимо для приложений, хранящих идентификаторы в базе данных. Извлечение сообщений по требованию - эффективный способ избежать обхода всего хранилища каждый раз, чтобы найти конкретное сообщение для извлечения. Свойство [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) класса [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) получает идентификатор записи сообщения. Переопределенный метод [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) получает сообщение из OLM. Следующий код-фрагмент демонстрирует использование этих функций:

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Получение пути к папке**

Вы также можете получить путь к папке папок в файле OLM. Aspose.Email предоставляет свойство [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/), которое возвращает путь к папке. Следующий код-фрагмент демонстрирует использование свойства [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) для получения путей к папкам в файле OLM.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // вывести текущий путь к папке
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

## **Подсчет количества элементов в папке**

Вы также можете подсчитать количество элементов в папке. Aspose.Email предоставляет свойство [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/), которое возвращает количество элементов в папке. Следующий код-фрагмент демонстрирует использование свойства [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) для получения количества элементов в папках файла OLM.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Количество сообщений [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Получение общего количества элементов OlmStorage**

Класс [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) также имеет метод [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/), который возвращает общее количество элементов сообщений, содержащихся в хранилище OLM.
  
```cs
using (var olm = new OlmStorage("storage.olm"))
{
    var count = olm.GetTotalItemsCount();
}
```

### **Извлечение сообщений из OLM по идентификаторам**
  
Иногда необходимо извлекать выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщение по требованию. Это эффективный способ избежать обхода всего хранилища каждый раз, чтобы найти конкретное сообщение для извлечения. Эта функция доступна для хранилищ OLM.

Код ниже показывает, как извлекать сообщения из OLM по идентификаторам.

Код выполняет следующие шаги:

1. Инициирует цикл foreach для итерации по списку объектов [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/). Цикл использует метод [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/) объекта olmFolder для получения списка всех сообщений в текущей папке, по которой выполняется итерация.
2. Цикл извлекает соответствующий объект MapiMessage из хранилища, вызывая метод [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), передавая идентификатор записи текущего сообщения в качестве параметра.

Полученный объект MapiMessage может быть использован для доступа и манипуляции содержимым сообщения. Цикл продолжается до обработки всех сообщений в папке.

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```
## **Получение цветов категорий Outlook**

Для работы с цветами категорий или категориями элементов Outlook, хранящимися в файлах OLM, Aspose.Email предлагает следующие решения:

- Класс [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) - представляет категории элементов Outlook, которые доступны по их имени и ассоциированным цветам, представленным в шестнадцатеричном формате.
- Метод [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) - извлекает список категорий.

Следующий пример кода демонстрирует, как получить все используемые категории из хранилища OLM:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
    
    foreach (var category in categories)
    {
        Console.WriteLine($"Имя категории: {category.Name}");
        
        // Цвет представлен в виде шестнадцатеричного значения: #rrggbb
        Console.WriteLine($"Цвет категории: {category.Color}");
    }
}
```
Пример кода ниже показывает, как получить цвет категории сообщения:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Имя категории: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Цвет категории: {categoryColor}");
        }
    }
}
```