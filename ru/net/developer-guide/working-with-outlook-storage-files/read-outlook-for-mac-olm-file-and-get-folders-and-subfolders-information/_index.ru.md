---
title: "Прочитайте файл Outlook для Mac OLM и получите информацию о папках и подпапках"
url: /ru/net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM — это особый формат файлов, используемый Microsoft Outlook для хранения локальных данных, таких как электронные письма, вложения, заметки, данные календаря, контакты, задачи, история и многое другое. Файлы OLM совместимы только с Outlook для Mac, и их нельзя открыть или получить к ним доступ в Outlook для Windows, который вместо этого использует формат файлов PST.

## **Открытие файлов формата OLM**

Файлы формата OLM можно открыть двумя способами:

- с помощью конструктора
- используя статический метод fromFile

Между этими методами существуют различия в поведении. См. раздел ниже.

### **Открытие файлов конструктором**

Чтобы открыть файл, вызовите конструктор [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс и передайте ему полное имя файла или поток в качестве аргумента:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

### **Открытие файлов статическим методом FromFile**

Чтобы открыть файл, используйте статический метод [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) и передайте ему полное имя файла или поток в качестве аргумента:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

## **Получение папок**

Чтобы получить доступ к структуре каталогов файла OLM, создайте экземпляр [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс, используя свой конструктор, и укажите путь к файлу.
Как только файл будет открыт, откройте его структуру каталогов, используя [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) имущество. Это свойство возвращает список [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) объекты, каждый из которых представляет собой каталог в файле OLM.
Для дальнейшего изучения структуры каталогов перейдите к [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) свойство каждого объекта, возвращающее список его подкаталогов. Используя эти свойства, вы можете перемещаться по всей иерархии каталогов файла OLM и получать доступ ко всем содержащимся в нем каталогам и подкаталогам.

В приведенном ниже примере показан список всех папок в иерархическом порядке:

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

При использовании [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) метод открытия файла OLM, [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) свойство не будет инициализировано по умолчанию и вернет значение null. В этом случае явным образом вызовите метод getFolders для инициализации [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) свойство и извлеките список каталогов в файле OLM:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

Кроме того, можно получить любую папку по имени:

1. Call [GetFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/getfolder/) method.
2. Передайте имя папки в качестве первого аргумента и значение, указывающее, следует ли игнорировать учет регистра при поиске папки, в качестве второго параметра.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // get inbox folder by name
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

## **Список электронных писем**

[OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) класс, представляющий собой папку, имеет следующие методы получения списка писем:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) реализует итерацию писем в папке. В этом случае каждая итерация возвращается [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) объект, который предоставляет краткую информацию об электронной почте.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), также реализует итерацию писем в папке, но в этом случае каждая итерация возвращается [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) объект, представляющий собой само электронное письмо со всеми свойствами.

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
        // save message in MSG format
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Другие полезные свойства**

Другие полезные свойства класса OlmFolder: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) and [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) свойства, которые возвращают наличие сообщений в папке и их количество.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Message count: {folder.MessageCount}");
    }
}
```
### **Получите или установите дату изменения сообщения**

Дата изменения представляет собой дату и время последнего изменения сообщения OLM. Вы можете использовать [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) свойство для получения или обновления измененного значения даты сообщения OLM.

Вот пример, демонстрирующий использование свойства:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```
## **Извлечение электронных писем**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс имеет [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/) метод, позволяющий извлекать электронные письма. Этот метод получает [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) object.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Extracts today's messages form Inbox
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```
## **Извлечение всех элементов из электронного письма с помощью Traversal API**

Вы можете извлечь все элементы из файла Outlook OLM, насколько это возможно, без исключения, даже если некоторые данные исходного файла повреждены. Для этого используйте [Хранилище OLM (обратный вызов по обходу исключений)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) конструктор и [Загрузить (строковое имя файла)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) метод вместо метода FromFile. Конструктор позволяет определить метод обратного вызова.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
```
Метод обратного вызова делает доступными исключения для загрузки и обхода.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) метод возвращает значение true, если файл был успешно загружен и возможен дальнейший обход. Если файл поврежден и обход невозможен, возвращается значение false.

```cs
if (olm.Load(fileName))
```

Следующий фрагмент кода и инструкции показывают, как использовать этот API:

1. Создайте новый экземпляр [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс, передающий обратный вызов по обработке исключений для обработки любых исключений, обнаруженных в процессе.
2. Загрузите файл OLM, вызвав [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) метод экземпляра OLMStorage.
3. Если файл OLM успешно загружен, получите иерархию папок, вызвав [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) метод на экземпляре OLMStorage. Это возвращает список объектов OLMFolder.
4. Вызовите метод ExtractItems, передав экземпляр OLMStorage и список объектов OlmFolder.
5. В методе ExtractItems выполните итерацию по каждой папке в списке папок.
6. Если папка содержит сообщения (электронные письма), напечатайте имя папки на консоли с помощью Console.WriteLine (папка).
7. Просмотрите сообщения в текущей папке, вызвав метод EnumerateMessages на экземпляре OlmStorage и передав текущую папку в качестве аргумента.
8. Напечатайте тему каждого сообщения на консоль с помощью Console.WriteLine (msg.Subject).
9. Если в папке есть подпапки, снова рекурсивно вызовите метод ExtractItems, передав экземпляр OlmStorage и подпапки текущей папки.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
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

Процесс извлечения электронной почты стал проще благодаря возможности извлекать выбранные сообщения OLM по идентификаторам. Это актуально для приложений, хранящих идентификаторы в базе данных. Извлечение сообщений по запросу — это эффективный способ избежать необходимости каждый раз искать нужное сообщение по всему хранилищу. [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) собственность [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) класс получает идентификатор записи сообщения. Перегруженный [Извлечь сообщение MAPI (идентификатор строки)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) метод [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс получает сообщение от OLM. Следующий фрагмент кода демонстрирует использование этих функций:

```cs
foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
{
    MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
}
```

## **Получить путь к папке**

Вы также можете получить путь к папкам в файле OML. Aspose.Email предоставляет [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) свойство, возвращающее путь к папке. Следующий фрагмент кода демонстрирует использование [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) свойство для получения путей к папкам в файле OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // print the current folder path
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

## **Подсчитайте количество элементов в папке**

Можно также подсчитать количество элементов в папке. Aspose.Email предоставляет [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) свойство, возвращающее количество элементов в папке. Следующий фрагмент кода демонстрирует использование [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) свойство для получения количества элементов в папках файла OML.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Message Count [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Узнайте общее количество товаров в OlmStorage**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс также имеет [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) метод, который возвращает общее количество сообщений, содержащихся в хранилище OLM.
 
```cs
  using (var olm = new OlmStorage("storage.olm"))
  {
     var count = olm.GetTotalItemsCount();
  }
```

### **Извлечение сообщений из OLM по идентификаторам**
 
Иногда требуется извлечь выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщение по запросу. Это эффективный способ избежать необходимости каждый раз просматривать все хранилище в поисках нужного сообщения для извлечения. Эта функция доступна для хранилищ OLM.

В приведенном ниже коде показано, как извлекать сообщения из OLM по идентификаторам.

Код выполняет следующие шаги:

1. Инициирует цикл foreach для итерации по списку [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) объекты. В цикле используется [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/) метод объекта OlmFolder для получения списка всех сообщений в текущей итерируемой папке.
2. Цикл извлекает соответствующий объект MapiMessage из хранилища, вызывая [Извлечь сообщение MAPI (идентификатор строки)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) метод [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс, проходящий через [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) текущего сообщения в качестве параметра.

Полученный объект MapiMessage можно использовать для доступа к содержимому сообщения и управления им. Цикл продолжается до тех пор, пока все сообщения в папке не будут обработаны.

```cs
  foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
  {
      MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
  }
```
## **Извлечение цветов категорий Outlook**

Для работы с цветами категорий или категориями элементов Outlook, хранящимися в файлах OLM, Aspose.Email предлагает следующие решения:

- [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) class — представляет категории элементов Outlook, доступные по названию и соответствующим цветам в шестнадцатеричном формате.
- [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) метод [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class - возвращает список категорий.

В следующем примере кода показано, как получить все используемые категории из хранилища OML:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
   
    foreach (var category in categories)
    {
        Console.WriteLine($"Category name: {category.Name}");
       
		//Color is represented as a hexadecimal value: #rrggbb
        Console.WriteLine($"Category color: {category.Color}");
    }
}
```
В приведенном ниже примере кода показано, как получить цвет категории сообщения:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Category name: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Category color: {categoryColor}");
        }
    }
}
```
