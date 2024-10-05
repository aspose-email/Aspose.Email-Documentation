---
title: "Работа с сообщениями в файле PST"
url: /ru/python-net/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---

## **Добавление сообщений в файлы PST**
Создание нового файла PST и добавление подпапок показало, как создать файл PST и добавить подкаталог к нему. С помощью Aspose.Email вы можете добавлять сообщения в подпапки файла PST, который вы создали или загрузили. В этой статье добавляются два сообщения с диска в подпапку "Входящие" файла PST. Используйте классы PersonalStorage и FolderInfo, чтобы добавлять сообщения в файлы PST. Чтобы добавить сообщения в папку "Входящие" файла PST:

1. Создайте экземпляр класса FolderInfo и загрузите его содержимое из папки "Входящие".
1. Добавьте сообщения с диска в папку "Входящие", вызвав метод FolderInfo.add_message(). Класс FolderInfo предоставляет метод add_messages, который позволяет добавлять большое количество сообщений в папку, уменьшая операции ввода-вывода на диск и улучшая производительность. Полный пример можно найти ниже, в разделе Добавление массовых сообщений.

Приведенные ниже фрагменты кода показывают, как добавить сообщения в подпапку PST с названием "Входящие".

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Добавление массовых сообщений**
Добавление отдельных сообщений в PST подразумевает больше операций ввода-вывода на диск и, следовательно, может замедлить производительность. Для повышения производительности сообщения могут добавляться в PST в пакетном режиме, чтобы минимизировать операции ввода-вывода. Метод add_messages позволяет определить диапазон сообщений, добавляемых в PST для улучшения производительности, и может использоваться в следующих сценариях.
### **Загрузка сообщений с диска**
Следующий фрагмент кода показывает, как загружать сообщения с диска.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Использование
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **Реализация MapiMessageCollection**
Следующий фрагмент кода показывает, как реализовать MapiMessageCollection.

```py
import os
from aspose.email.mapi import MapiMessage


class MapiMessageEnumerator:
    def __init__(self, path):
        self.files = os.listdir(path)
        self.position = -1

    def __next__(self):
        self.position += 1
        if self.position < len(self.files):
            return MapiMessage.from_file(os.path.join(self.path, self.files[self.position]))
        else:
            raise StopIteration

    def __iter__(self):
        return self


class MapiMessageCollection:
    def __init__(self, path):
        self.path = path

    def __iter__(self):
        return MapiMessageEnumerator(self.path)


# Использование
msg_folder_name = "\\Files\\msg"

message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Сделать что-то с каждым MapiMessage
    pass
```
### **Добавление сообщений из другого PST**
Для добавления сообщений из другого PST используйте метод FolderInfo.enumerate_mapi_messages(). Следующий фрагмент кода показывает, как добавить сообщения из других PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Получение информации о сообщениях из файла Outlook PST**
В разделе Чтение файла PST Outlook и получение информации о папках и подпапках мы обсудили загрузку файла PST Outlook и просмотр его папок для получения имен папок и количества сообщений в них. Эта статья объясняет, как прочитать все папки и подпапки в файле PST и отобразить информацию о сообщениях, например, тему, отправителя и получателей. Файл PST Outlook может содержать вложенные папки. Чтобы получить информацию о сообщениях из них, а также из папок верхнего уровня, используйте рекурсивный метод для чтения всех папок. Следующий фрагмент кода показывает, как читать файл PST Outlook и рекурсивно отображать содержимое папки и сообщений.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Извлечение сообщений из файлов PST**

Эта статья показывает, как читать файлы PST Microsoft Outlook и извлекать сообщения. Ниже приведен фрагмент кода, показывающий, как извлечь сообщения из файла PST.

```python
from aspose.email.storage.pst import *
from aspose.email.mapi import MapiMessage

pst = PersonalStorage.from_file("Outlook.pst")

folderInfo = pst.root_folder

messageInfoCollection = folderInfo.get_contents()

for messageInfo in messageInfoCollection:
   mapi = pst.extract_message(messageInfo)

   print("Тема: " + mapi.subject)
   print("Имя отправителя: " + mapi.sender_name)
   print("Электронная почта отправителя: " + mapi.sender_email_address)
   print("Кому: ", mapi.display_to)
   print("Копия: ", mapi.display_cc)
   print("Скрытая копия: ", mapi.display_bcc)
   print("Время доставки: ", str(mapi.delivery_time))
   print("Тело: " + mapi.body)
```
### **Извлечение n количества сообщений из файла PST**

Чтобы извлечь определенное количество сообщений из файла PST, используйте метод *get_contents(start_index, count)* класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Он принимает два параметра:

- **start_index** - номер стартового сообщения, например, 10-е;
- **count** - общее количество сообщений для извлечения.

Извлечение только необходимого подмножества сообщений за один раз может быть полезным для управления большими объемами данных электронной почты. Следующий пример кода демонстрирует реализацию этой функции:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Извлекает сообщения, начиная с 10 индекса и извлекает всего 100 сообщений
messages = folder.get_contents(10, 100)
```
### **Получение общего количества элементов из файла PST**

Чтобы получить общее количество элементов (таких как электронные письма, встречи, задачи, контакты и т. д.), присутствующих в хранилище сообщений, используйте метод *get_total_items_count()* класса [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Он предоставляет удобный способ быстро собирать информацию о размере и объеме данных внутри хранилища. Следующий фрагмент кода показывает, как получить общее количество элементов из файла PST:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Удаление сообщений из файлов PST**
Добавление сообщений в файлы PST показало, как добавлять сообщения в файлы PST. Конечно, также возможно удалить элементы (содержимое) из файла PST, и может быть желательно удалить сообщения оптом. Элементы из файла PST можно удалить с помощью метода FolderInfo.delete_child_item(). API также предоставляет метод FolderInfo.delete_child_items() для удаления элементов оптом из файла PST.
### **Удаление сообщений из файлов PST**
Эта статья показывает, как использовать класс FolderInfo для доступа к конкретным папкам в файле PST. Чтобы удалить сообщения из подпапки "Отправленные" ранее загруженного или созданного файла PST:

1. Создайте экземпляр класса FolderInfo и загрузите его содержимое из подпапки "Отправленные".
1. Удалите сообщения из папки "Отправленные", вызвав метод FolderInfo.delete_child_item() и передав в качестве параметра MessageInfo.entry_id. Следующий фрагмент кода показывает, как удалить сообщения из подпапки "Отправленные" файла PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Удаление папок из файлов PST**

Вы можете удалить папку PST, переместив ее в папку "Удаленные элементы".

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Пустая папка")
some_folder = pst.root_folder.get_sub_folder("Некоторая папка")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
Преимущество этого метода заключается в том, что удаленная папка может быть легко восстановлена.

```python
some_folder = pst.root_folder.get_sub_folder("Некоторая папка")
pst.move_item(some_folder, pst.root_folder)
```
Вы также можете навсегда удалить папку из папки "Удаленные элементы", если это необходимо.

```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
Метод *delete_child_item* можно использовать для любых папок, если вы хотите немедленно и навсегда удалить подпапку, обходя папку "Удаленные элементы".

```python
some_folder = pst.root_folder.get_sub_folder("Некоторая папка")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Удаление элементов из PST**

Во многих системах обмена сообщениями или почтовых клиентах каждому элементу (например, электронному письму, встрече или задаче) присваивается уникальный идентификатор, называемый идентификатором записи. Метод *delete_item(entry_id)* класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) принимает этот идентификатор записи в качестве параметра и удаляет соответствующий элемент из хранилища сообщений. Используйте следующий код для удаления элемента из хранилища сообщений:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Удаление элементов оптом из файла PST**
API Aspose.Email может использоваться для удаления элементов оптом из файла PST. Это достигается с помощью метода delete_child_items(), который принимает список идентификаторов записи, относящихся к элементам, которые необходимо удалить. Следующий фрагмент кода показывает, как удалять элементы оптом из файла PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Поиск сообщений и папок в PST по критериям**
Файлы личного хранилища (PST) могут содержать огромное количество данных, и поиск данных, которые соответствуют определенному критерию в таких крупных файлах, требует включения множества контрольных точек в код для фильтрации информации. С помощью класса PersonalStorageQueryBuilder Aspose.Email делает возможным поиск конкретных записей в PST на основе заданного критерия поиска. PST можно искать по сообщениям на основе такие параметры поиска, как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. Класс PersonalStorageQueryBuilder также может использоваться для поиска подпапок.
### **Поиск сообщений и папок в PST**
Следующий фрагмент кода показывает, как использовать класс PersonalStorageQueryBuilder для поиска содержимого в PST на основе различных критериев поиска. Например, он показывает поиск PST на основе:

- Важности сообщения.
- Класса сообщения.
- Наличия вложений.
- Размер сообщения.
- Непрочитанных сообщений.
- Непрочитанных сообщений с вложениями, и
- папок с конкретным названием подпапки.

```py
from aspose.email.mapi import MapiMessageFlags
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder, MapiImportance

with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")
    builder = PersonalStorageQueryBuilder()

    # Сообщения с высокой важностью
    builder.importance.equals(2)
    messages = folder.get_contents(builder.get_query())
    print("Сообщения с высокой важностью:", messages.count)

    builder = PersonalStorageQueryBuilder()
    builder.message_class.equals("IPM.Note")
    messages = folder.get_contents(builder.get_query())
    print("Сообщения с IPM.Note:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Сообщения с вложениями И с высокой важностью
    builder.importance.equals(2)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Сообщения с вложениями:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Сообщения размером > 15 КБ
    builder.message_size.greater(15000)
    messages = folder.get_contents(builder.get_query())
    print("Сообщения размером > 15 КБ:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Непрочитанные сообщения
    builder.has_no_flags(MapiMessageFlags.READ)
    messages = folder.get_contents(builder.get_query())
    print("Непрочитанные:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Непрочитанные сообщения с вложениями
    builder.has_no_flags(MapiMessageFlags.READ)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Непрочитанные сообщения с вложениями:", messages.count)

    # Папка с названием 'SubInbox'
    builder = PersonalStorageQueryBuilder()
    builder.folder_name.equals("SubInbox")
    folders = folder.get_sub_folders(builder.get_query())
    print("Папка, имеющая подпапку:", folders.count)

    builder = PersonalStorageQueryBuilder()
    # Папки с подпапками
    builder.has_subfolders()
    folders = folder.get_sub_folders(builder.get_query())
    print("Папки с подпапками:", folders.count)
```
### **Поиск строки в PST с параметром игнорирования регистра**
Следующий фрагмент кода показывает, как искать строку в PST с параметром игнорирования регистра.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Поиск тем сообщений по нескольким ключевым словам в файле PST**

Извлечение конкретных сообщений или элементов из файла личного хранения (PST) или хранилища сообщений путем реализации метода *either(query1, query2)* класса [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) в вашем проекте. Он принимает два параметра, позволяющих объединить два разных запроса: query1 и query2 и найти тему сообщения, соответствующую любому из двух указанных слов. См. пример кода ниже:

```python
import aspose.email as ae

builder1 = ae.storage.pst.PersonalStorageQueryBuilder()
builder1.subject.contains("Review") # 'Review' - ключевое слово для поиска

builder2 = ae.storage.pst.PersonalStorageQueryBuilder()
builder2.subject.contains("Error") # 'Error' - также ключевое слово для поиска

builder = ae.storage.pst.PersonalStorageQueryBuilder()
# темы сообщений должны содержать слова 'Review' или 'Error'
builder.either(builder1.get_query(), builder2.get_query())


pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")
messages = folder.get_contents(builder.get_query())

for message in messages:
    print(f"Сообщение: {message.subject}")
```

## **Перемещение элементов в другие папки файла PST**
Aspose.Email делает возможным перемещение элементов из одной папки в другую в том же файле личного хранилища (PST). Это включает:

- Перемещение указанной папки в новый родительский каталог.
- Перемещение указанных сообщений в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подпапок в новый родительский каталог.

Следующий фрагмент кода показывает, как перемещать элементы, такие как сообщения и папки, из одной папки в другую в том же файле PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Обновление свойств сообщений в файле PST**
Иногда требуется обновить определенные свойства сообщений, такие как изменение темы, маркировка важности сообщений и аналогичные другие. Обновление сообщения в файле PST с такими изменениями в свойствах сообщения можно достичь с помощью метода FolderInfo.change_messages. Эта статья показывает, как обновить сообщения оптом в файле PST для изменений в свойствах. Следующий фрагмент кода показывает, как обновить свойства сообщений в пакетном режиме для нескольких сообщений в файле PST.

```py
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder
from aspose.email.mapi import MapiPropertyTag, MapiProperty, MapiPropertyCollection

pst_file_path = data_dir + "ya4demia04vb.pst"

# Загрузка файла PST Outlook
with PersonalStorage.from_file(pst_file_path) as personal_storage:
    # Получите необходимую подпапку
    inbox = personal_storage.root_folder.get_sub_folder("Inbox")

    # Найти сообщения, у которых From = "someuser@domain.com"
    query_builder = PersonalStorageQueryBuilder()
    query_builder.from_address.contains("someuser@domain.com")

    # Получить содержимое из запроса
    messages = inbox.get_contents(query_builder.get_query())

    # Сохраните (MessageInfo, EntryIdString) в список
    change_list = [message_info.entry_id_string for message_info in messages]

    # Составьте новые свойства
    updated_properties = MapiPropertyCollection()
    updated_properties.add(
        MapiPropertyTag.SUBJECT_W,
        MapiProperty(MapiPropertyTag.SUBJECT_W, "Новая тема".encode("utf-16le"))
    )
    updated_properties.add(
        MapiPropertyTag.IMPORTANCE,
        MapiProperty(MapiPropertyTag.IMPORTANCE, bytearray([0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]))
    )

    # Обновить сообщения с From = "someuser@domain.com" новыми свойствами
    inbox.change_messages(change_list, updated_properties)
```
## **Обновление пользовательских свойств в файле PST**
Иногда требуется отметить элементы, которые обработаны в файле PST. API Aspose.Email позволяет достичь этого с помощью MapiProperty и MapiNamedProperty. Следующие методы полезны для достижения этого.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- FolderInfo.change_messages(MapiPropertyCollection updatedProperties) - изменяет все сообщения в папке
- PersonalStorage.change_messages(string entryId, MapiPropertyCollection updatedProperties) - изменяет свойства сообщения

```py
from uuid import UUID
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import MapiNamedProperty, MapiPropertyCollection
from aspose.email.mapi import MapiPropertyType, MapiProperty, MapiPropertyTag

def generate_named_property_tag(index, data_type):
    return (((0x8000 | index) << 16) | data_type) & 0x00000000FFFFFFFF

def run():
    # Загрузка файла Outlook
    pst_file_path = data_dir + "my.pst"

    with PersonalStorage.from_file(pst_file_path) as personal_storage:
        test_folder = personal_storage.root_folder.get_sub_folder("Inbox")

        # Создание коллекции свойств сообщения для добавления или обновления
        new_properties = MapiPropertyCollection()

        # Обычные, пользовательские и именованные свойства PidLidLogFlags
        mapi_property = MapiProperty(
            MapiPropertyTag.ORG_EMAIL_ADDR_W,
            "test_address@org.com".encode("utf-16le")
        )
        named_property1 = MapiNamedProperty(
            generate_named_property_tag(0, MapiPropertyType.LONG),
            "ITEM_ID",
            UUID("00000000-0000-0000-0000-000000000000"),
            bytearray([0x7B, 0x00, 0x00, 0x00])
        )
        named_property2 = MapiNamedProperty(
            generate_named_property_tag(1, MapiPropertyType.LONG),
            0x0000870C,
            UUID("0006200A-0000-0000-C000-000000000046"),
            bytearray([0x00, 0x00, 0x00, 0x00])
        )
        new_properties.add(named_property1.tag, named_property1)
        new_properties.add(named_property2.tag, named_property2)
        new_properties.add(mapi_property.tag, mapi_property)
        test_folder.change_messages(test_folder.enumerate_messages_entry_id(), new_properties)

# Использование
run()
```
## **Извлечение вложений без извлечения полного сообщения**
API Aspose.Email можно использовать для извлечения вложений из сообщений PST без предварительного извлечения полного сообщения. Метод extract_attachments класса IEWSClient можно использовать для этого. Следующий фрагмент кода показывает, как извлечь вложения без извлечения полного сообщения.

```py
from aspose.email.storage.pst import PersonalStorage


with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")

    for message_info in folder.enumerate_messages_entry_id():
        attachments = personal_storage.extract_attachments(message_info)

        if attachments.count != 0:
            for attachment in attachments:
                if attachment.long_file_name is not None and attachment.long_file_name.endswith(".msg"):
                    continue
                else:
                    attachment.save(data_dir + attachment.long_file_name)
```
## **Добавление файлов в PST**
Ключевая функция Microsoft Outlook заключается в управлении электронной почтой, календарями, задачами, контактами и записями журнала. Кроме того, файлы также могут быть добавлены в папку PST, и полученный PST сохраняет учетные данные добавленных документов. Aspose.Email предоставляет возможность добавлять файлы в папку аналогично добавлению сообщений, контактов, задач и записей журнала в PST. Следующий фрагмент кода показывает, как добавлять документы в папку PST с помощью Aspose.Email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}