---
title: "Чтение файла OLM Outlook для Mac и получение информации о папках и подпапках"
url: /ru/python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 120
type: docs
---

OLM (архив Outlook для Mac) — это формат файла, связанный с Microsoft Outlook для Mac. Он используется для архивирования и хранения электронных писем, контактов, элементов календаря, задач и других данных Outlook на компьютерах Mac. Файлы OLM служат форматом резервного копирования или архивирования, позволяя пользователям сохранять свои данные Outlook для Mac для последующего использования или миграции. Важно отметить, что файлы OLM специфичны для Outlook для Mac и не совместимы с форматом файла PST (личная таблица хранения), используемым в Outlook на Windows. Если вам нужно передать данные Outlook между разными платформами, удобны инструменты конвертации. Aspose.Email предлагает такие инструменты, включая открытие, чтение и другие функции для работы с файлами OLM.

## **Открытие файлов формата OLM**

Файлы формата OLM можно открывать двумя способами:

- с использованием конструктора
- с использованием статического метода 'from_file'

### **Открытие файлов с помощью конструктора**

Чтобы открыть файл, вызовите конструктор класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) и передайте полное имя файла или поток в качестве аргумента:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Открытие файлов с использованием статического метода FromFile**

Чтобы открыть файл, используйте статический метод 'from_file' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) и передайте полное имя файла или поток в качестве аргумента:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Получение папок**

Вы можете визуализировать и отображать иерархию папок, извлеченную из файла OLM, с помощью функции 'print_all_folders'. Она принимает свойство 'folder_hierarchy' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) и уровень отступа в качестве входных данных, после чего рекурсивно проходит по иерархии, чтобы напечатать имя каждой папки с соответствующим отступом. Пример кода ниже демонстрирует, как использовать эту функцию для отображения иерархии папок из файла OLM. Он отображает список всех папок в иерархическом порядке:

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

Пример кода выше предназначен для отображения иерархии папок файла OLM с помощью рекурсивной функции в более структурированном и читаемом формате. Aspose.Email также позволяет напрямую обращаться к структуре папок из файла OLM с помощью метода 'get_folders()' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class).

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Кроме того, можно получить любую папку по имени. Следующий пример кода использует метод 'get_folder(name, ignore_case)' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class), передавая имя папки и параметры чувствительности к регистру для извлечения папки по ее имени:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **Список электронных писем**

Примеры кода ниже демонстрируют, как использовать библиотеку Aspose.Email для чтения и извлечения тем писем из файла Outlook для Mac (OLM). Класс [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class), который представляет папку, имеет следующие методы для получения списка электронных писем:

- 'enumerate_messages()' - Итерирует через каждое электронное письмо в папке. Этот метод возвращает сообщения в виде экземпляров класса [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class), который предоставляет основную информацию о каждом электронном письме, такую как тема, отправитель, дата и т. д.
- 'enumerate_mapi_messages()' - Также итерирует через каждое электронное письмо в папке, но в этом случае возвращает сообщения в виде экземпляров класса [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class), который представляет электронное письмо более подробно и специфично для MAPI. Он предоставляет доступ к широкому спектру свойств и деталей электронного письма, что позволяет выполнять более сложную и специализированную обработку.

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

Другие полезные свойства класса [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) включают:

- 'has_messages' - Получает значение, указывающее, есть ли в текущей папке сообщения.
- 'message_count' - Получает общее количество сообщений.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Count of messages: {folder.message_count}")
```

### **Получить или установить дату последнего изменения сообщения**

Вы можете получить информацию о времени последнего изменения электронного письма. Свойство 'modified_date' класса [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) представляет дату и время последнего изменения сообщения.

Вот пример, который демонстрирует использование этого свойства:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Извлечение электронных писем**

Вы можете извлечь фактические данные сообщения MAPI из хранилища электронной почты. Метод 'extract_mapi_message(message_info)' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) используется для извлечения сообщения MAPI из хранилища на основе предоставленного message_info.

Пример кода ниже демонстрирует, как использовать этот метод:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
```

## **Извлечение всех элементов из электронной почты с помощью Traversal API**

Вы можете извлечь все элементы из файла OLM Outlook насколько это возможно, не выбрасывая исключения, даже если некоторые данные оригинального файла повреждены. Для этого используйте конструктор [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) и метод [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) вместо метода FromFile. Конструктор позволяет определить метод обратного вызова.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Код для обработки исключений. */ }))
```
Метод обратного вызова делает доступными исключения загрузки и обхода.

Метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) возвращает 'true', если файл был успешно загружен и дальнейший обход возможен. Если файл поврежден и нет возможности для обхода, возвращается 'false'.

```cs
if (olm.Load(fileName))
```

Следующий фрагмент кода и шаги показывают, как использовать этот API:

1. Создайте новый экземпляр класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/), передавая метод обратного вызова для обработки любых исключений, встречающихся в процессе.
2. Загрузите файл OLM, вызвав метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) экземпляра OlmStorage.
3. Если файл OLM успешно загружен, получите иерархию папок, вызвав метод [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) на экземпляре OlmStorage. Это возвращает список объектов OlmFolder.
4. Вызовите метод ExtractItems, передавая экземпляр OlmStorage и список объектов OlmFolder.
5. В методе ExtractItems итеративно пройдитесь по каждой папке в списке папок.
6. Если папка содержит сообщения (электронные письма), выведите имя папки в консоль, используя Console.WriteLine(folder).
7. Итерируйте через сообщения в текущей папке, вызывая метод EnumerateMessages на экземпляре OlmStorage, передавая текущую папку в качестве аргумента.
8. Выведите тему каждого сообщения в консоль, используя Console.WriteLine(msg.Subject).
9. Если у папки есть подпапки, рекурсивно вызовите метод ExtractItems снова, передавая экземпляр OlmStorage и подпапки текущей папки.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Код для обработки исключений. */ }))
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

Чтобы получить доступ к данным сообщения MAPI, вы можете использовать свойство 'entry_id' для получения уникального идентификатора (Entry ID) сообщения с помощью класса [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class). Затем вы можете использовать метод 'extract_mapi_message(id)' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class), передавая идентификатор в качестве параметра для получения сообщения MAPI, связанного с этим конкретным идентификатором. Следующий фрагмент кода демонстрирует использование этих возможностей:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Получение пути папки**

Вы также можете получить иерархический путь или расположение папки внутри файла Outlook OLM. Aspose.Email предоставляет свойство 'path' класса [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class), которое возвращает путь к папке. Следующий фрагмент кода демонстрирует использование этого свойства:

```py
import aspose.email as ae


def print_path(storage, folders):
    for folder in folders:
        # напечатать текущий путь папки
        print(folder.path)

        if folder.sub_folders:
            print_path(storage, folder.sub_folders)


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_path(olm, olm.folder_hierarchy)
```

## **Подсчет количества элементов в папке**

Aspose.Email предоставляет возможность подсчитывать общее количество электронных писем, содержащихся в конкретной папке файла Outlook OLM. Свойство 'message_count' класса [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) возвращает общее количество элементов (электронных писем), хранящихся в конкретной папке файла OLM. Следующий пример кода демонстрирует использование этого свойства:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Количество сообщений [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Получить общее количество элементов OlmStorage**

Метод 'get_total_items_count()' класса [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) возвращает общее количество элементов сообщений, содержащихся в хранилище OLM.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Извлечение цветовых категорий Outlook**

С помощью Aspose.Email вы можете легко извлечь и использовать цветовые категории, связанные с категориями элементов Outlook, хранящимся в OLM файлах. Класс [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) позволяет получать названия категорий и их соответствующие цвета, представленные в шестнадцатеричном формате. Класс [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) содержит метод 'GetCategories()', предназначенный для извлечения списка категорий из хранилища OLM. Реализуя приведенный ниже пример кода, вы можете легко извлечь все используемые категории из файла OLM и получить название категории вместе с ее цветом.

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
    
    for category in categories:
        print(f"Название категории: {category.Name}")
        
        # Цвет представлен в шестнадцатеричном формате: #rrggbb
        print(f"Цвет категории: {category.Color}")
```

Кроме того, вы можете получить цвет категории, связанный с конкретными сообщениями, итерируя через сообщения в папке и получая соответствующий цвет категории на основе названия категории.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Название категории: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Цвет категории: {categoryColor}")
```