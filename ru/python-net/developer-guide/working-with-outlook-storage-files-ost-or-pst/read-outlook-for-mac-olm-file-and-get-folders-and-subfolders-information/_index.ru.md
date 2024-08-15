---
title: "Прочитайте файл Outlook для Mac OLM и получите информацию о папках и подпапках"
url: /ru/python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM (архив Outlook для Mac) — это формат файла, связанный с Microsoft Outlook для Mac. Он используется для архивирования и хранения сообщений электронной почты, контактов, элементов календаря, задач и других данных Outlook на компьютерах Mac. Файлы OLM служат форматом резервного копирования или архивирования, что позволяет пользователям сохранять данные Outlook для Mac для последующего использования или переноса. Важно отметить, что файлы OLM специфичны для Outlook для Mac и несовместимы с форматом файлов PST (таблица персональных данных), используемым Outlook в Windows. Если вам нужно перенести данные Outlook между разными платформами, вам пригодятся инструменты конвертации. Aspose.Email предлагает такие инструменты, как открытие, чтение и другие функции для работы с файлами OLM.

## **Открытие файлов формата OLM**

Файлы формата OLM можно открыть двумя способами:

- с помощью конструктора
- используя статический метод from_file

### **Открытие файлов конструктором**

Чтобы открыть файл, вызовите конструктор [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс и передайте ему полное имя файла или поток в качестве аргумента:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Открытие файлов статическим методом FromFile**

Чтобы открыть файл, используйте статический метод from_file из [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс и передайте ему полное имя файла или поток в качестве аргумента:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Получение папок**

Вы можете визуализировать и отобразить иерархию папок, полученную из файла OLM, с помощью функции print_all_folders. Она принимает свойство folder_hierarchy, присвоенное параметру [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс и уровень отступа в качестве входных данных, затем рекурсивно перемещается по иерархии и печатает имя каждой папки вместе с соответствующим отступом. В приведенном ниже примере кода показано, как использовать эту функцию для отображения иерархии папок из файла OLM. Она отображает список всех папок в иерархическом порядке:

```py
import aspose.email as ae


def print_all_folders(folder_hierarchy, indent):
    for folder in folder_hierarchy:
        print(f"{indent}{folder.name}")
        print_all_folders(folder.sub_folders, indent + "-")

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_all_folders(olm.folder_hierarchy, "")
```

Приведенный выше пример кода предназначен для отображения иерархии папок файла OLM с помощью рекурсивной функции в более структурированном и читаемом формате. Aspose.Email также позволяет напрямую обращаться к структуре папок из файла OLM с помощью метода get_folders () в [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Кроме того, можно получить любую папку по имени. В следующем примере кода используется метод get_folder (name, ignore_case) [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс, передающий имя папки и чувствительность к регистру в качестве параметров для получения папки по ее имени:


```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **Список электронных писем**

В приведенных ниже фрагментах кода показано, как использовать библиотеку Aspose.Email для чтения и извлечения тем писем из файла Outlook для Mac (OLM). [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) класс, представляющий собой папку, имеет следующие методы получения списка писем:

- 'enumerate_messages () '- выполняет итерацию по каждому сообщению электронной почты в папке. Этот метод возвращает сообщения в виде экземпляров [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) класс, который предоставляет базовую информацию о каждом сообщении электронной почты, такую как тема, отправитель, дата и т. д.
- 'enumerate_mapi_messages () '— также выполняет итерацию по каждому сообщению электронной почты в папке, но в данном случае возвращает сообщения как экземпляры [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) класс, который представляет сообщение электронной почты более подробным и специфичным для MAPI способом. Он предоставляет доступ к широкому спектру свойств и деталей сообщения электронной почты, что позволяет выполнять более сложную и специализированную обработку.

### **Использование метода EnumerateMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    print(message_info.subject)
```

### **Использование метода EnumerateMapiMessages**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for msg in folder.enumerate_mapi_messages():
    msg.save(f"{msg.subject}.msg")
```

### **Другие полезные свойства**

Другие полезные свойства [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) класс таков:

- 'has_messages' — возвращает значение, указывающее, есть ли в текущей папке сообщения.
- 'message_count' - Определяет количество сообщений.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Message count: {folder.message_count}")
```

### **Получите или установите дату изменения сообщения**

Можно получить информацию о времени последнего изменения сообщения электронной почты. Свойство 'modified_date' [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) класс представляет дату и время последнего изменения сообщения.

Вот пример, демонстрирующий использование свойства:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Извлечение электронных писем**

Вы можете получить фактические данные сообщений MAPI из хранилища электронной почты. Метод 'extract_mapi_message (message_info) ' [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс используется для извлечения сообщения MAPI из хранилища на основе предоставленного message_info. 

В приведенном ниже примере кода показано, как использовать этот метод:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
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

Для доступа к данным сообщения MAPI вы можете использовать свойство 'entry_id' для получения уникального идентификатора (Entry ID) сообщения с помощью [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) класс. Затем вы можете использовать метод extract_mapi_message (id) [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс, передающий идентификатор записи в качестве параметра для получения сообщения MAPI, связанного с этим конкретным идентификатором записи. Следующий фрагмент кода демонстрирует использование этих функций:

```py

import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Получить путь к папке**

Вы также можете получить иерархический путь или местоположение папки в файле Outlook OLM. Aspose.Email предоставляет свойство «путь» [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) класс, возвращающий путь к папке. Следующий фрагмент кода демонстрирует использование этого свойства:

```py
import aspose.email as ae


def print_path(storage, folders):
    for folder in folders:
        # print the current folder path
        print(folder.path)

        if folder.sub_folders:
            print_path(storage, folder.sub_folders)


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_path(olm, olm.folder_hierarchy)
```

## **Подсчитайте количество элементов в папке**

Aspose.Email предоставляет возможность подсчета общего количества сообщений электронной почты, содержащихся в определенной папке файла Outlook OLM. Свойство 'message_count' [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) класс возвращает общее количество элементов (сообщений электронной почты), хранящихся в определенной папке файла OLM. Следующий фрагмент кода демонстрирует использование этого свойства:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Message Count [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Узнайте общее количество товаров в OlmStorage**

Метод get_total_items_count () [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) класс возвращает общее количество элементов сообщений, содержащихся в хранилище OLM.
 
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Извлечение цветов категорий Outlook**

С помощью Aspose.Email вы можете легко извлекать и использовать цвета категорий, связанные с категориями элементов Outlook, хранящимися в файлах OLM. [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) класс позволяет получить доступ к именам категорий и их соответствующим цветам, представленным в шестнадцатеричном формате. [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) в классе реализован метод getCategories () для получения списка категорий из хранилища OLM. Используя приведенный ниже пример кода, вы можете легко извлечь все используемые категории из файла хранилища OML и получить доступ к имени категории и ее цвету.

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
   
    for category in categories:
        print(f"Category name: {category.Name}")
       
        # Color is represented as a hexadecimal value: #rrggbb
        print(f"Category color: {category.Color}")
```

Кроме того, можно получить цвет категории, связанный с конкретными сообщениями, путем повторного просмотра сообщений в папке и выбора цвета соответствующей категории на основе названия категории.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Category name: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Category color: {categoryColor}")
```