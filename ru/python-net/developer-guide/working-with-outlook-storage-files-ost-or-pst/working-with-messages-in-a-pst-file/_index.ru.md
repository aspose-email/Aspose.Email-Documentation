---
title: "Работа с сообщениями в файле PST"
url: /ru/python-net/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---


## **Добавление сообщений в файлы PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавлять сообщения в подпапки созданного или загруженного файла PST. В этой статье два сообщения с диска добавляются во вложенную папку «Входящие» PST. Используйте классы PersonalStorage и FolderInfo для добавления сообщений в файлы PST. Чтобы добавить сообщения в папку «Входящие» файла PST, выполните следующие действия:

1. Создайте экземпляр класса FolderInfo и загрузите в него содержимое папки «Входящие».
1. Добавьте сообщения с диска в папку «Входящие», вызвав метод folderInfo.add_Message (). Класс FolderInfo предоставляет метод add_messages, который позволяет добавлять большое количество сообщений в папку, сокращая количество операций ввода-вывода на диск и повышая производительность. Полный пример можно найти ниже в разделе Добавление массовых сообщений.

В приведенных ниже фрагментах кода показано, как добавлять сообщения в подпапку PST под названием «Входящие».



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Добавление массовых сообщений**
Добавление отдельных сообщений в PST подразумевает большее количество операций ввода-вывода на диск и, следовательно, может снизить производительность. Для повышения производительности сообщения можно добавлять в PST в массовом режиме, чтобы минимизировать операции ввода-вывода. Метод add_messages позволяет определить диапазон сообщений, добавляемых в PST для повышения производительности, и может использоваться в следующих сценариях.
### **Загрузка сообщений с диска**
В следующем фрагменте кода показано, как загружать сообщения с диска.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Usage
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **Внедрение коллекции сообщений MAPI**
В следующем фрагменте кода показано, как реализовать MAPImessageCollection.

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


# Usage
msg_folder_name = "\\Files\\msg"

message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Do something with each MapiMessage
    pass
```
### **Добавление сообщений из других PST**
Для добавления сообщений из другого PST используйте метод folderInfo.enumerate_MAPI_Messages (). В следующем фрагменте кода показано, как добавлять сообщения из других PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Получение информации о сообщениях из файла Outlook PST**
В разделах «Чтение PST-файла Outlook» и «Получение сведений о папках и подпапках» мы рассмотрели загрузку файла Outlook PST и просмотр его папок для получения имен папок и количества сообщений в них. В этой статье описывается, как читать все папки и подпапки в файле PST и отображать информацию о сообщениях, например тему, отправителя и получателя. Файл Outlook PST может содержать вложенные папки. Чтобы получить информацию о сообщениях из этих папок, а также из папок верхнего уровня, используйте рекурсивный метод чтения всех папок. В следующем фрагменте кода показано, как читать PST-файл Outlook и рекурсивно отображать содержимое папки и сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Извлечение сообщений из файлов PST**

В этой статье показано, как читать файлы Microsoft Outlook PST и извлекать сообщения. Ниже приведен фрагмент кода, показывающий, как извлекать сообщения из файла PST.

```python
from aspose.email.storage.pst import *
from aspose.email.mapi import MapiMessage

pst = PersonalStorage.from_file("Outlook.pst")

folderInfo = pst.root_folder

messageInfoCollection = folderInfo.get_contents()

for messageInfo in messageInfoCollection:
   mapi = pst.extract_message(messageInfo)

   print("Subject: " + mapi.subject)
   print("Sender name: " + mapi.sender_name)
   print("Sender email address: " + mapi.sender_email_address)
   print("To: ", mapi.display_to)
   print("Cc: ", mapi.display_cc)
   print("Bcc: ", mapi.display_bcc)
   print("Delivery time: ", str(mapi.delivery_time))
   print("Body: " + mapi.body)
```
### **Извлечение n количества сообщений из PST-файла**

Чтобы извлечь определенное количество сообщений из файла PST, используйте *get_contents (начальный индекс, количество)* метод [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс. Он принимает два параметра:

- **start_index** - номер начального сообщения, например 10-е;
- **count** - общее количество сообщений, которые нужно получить.

Одновременное получение только необходимого подмножества сообщений может быть полезно для управления большими объемами данных электронной почты. Следующий пример кода демонстрирует реализацию этой функции:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Extracts messages starting from 10th index top and extract total 100 messages
messages = folder.get_contents(10, 100)
```
### **Получение общего количества элементов из файла PST**

Чтобы получить общее количество элементов (таких как электронные письма, встречи, задачи, контакты и т. д.), присутствующих в хранилище сообщений, используйте *get_total_items_count()* метод [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) класс. Он предоставляет удобный способ быстрого сбора информации о размере и объеме данных в хранилище. В следующем фрагменте кода показано, как получить общее количество элементов из файла PST:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Удалить сообщения из файлов PST**
В статье «Добавить сообщения в файлы PST» показано, как добавлять сообщения в файлы PST. Конечно, также можно удалять элементы (содержимое) из файла PST, и может быть желательно удалять сообщения массово. Элементы из файла PST можно удалить с помощью метода folderInfo.delete_child_Item (). API также предоставляет метод folderInfo.delete_child_items () для массового удаления элементов из файла PST.
### **Удаление сообщений из PST-файлов**
В этой статье показано, как использовать класс FolderInfo для доступа к определенным папкам в файле PST. Чтобы удалить сообщения из подпапки «Отправленные» ранее загруженного или созданного файла PST, выполните следующие действия:

1. Создайте экземпляр класса FolderInfo и загрузите в него содержимое отправленной вложенной папки.
1. Удалите сообщения из папки «Отправленные», вызвав метод folderInfo.delete_child_Item () и передав в качестве параметра MessageInfo.entry_ID. В следующем фрагменте кода показано, как удалять сообщения из подпапки Sent файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Удаление папок из файлов PST**

Папку PST можно удалить, переместив ее в папку «Удаленные».

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Empty folder")
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
Преимущество этого метода в том, что удаленную папку можно легко восстановить.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```
При необходимости можно также навсегда удалить папку из папки «Удаленные».


```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
The *delete_child_item* метод можно использовать для любых папок, если вы хотите немедленно и навсегда удалить подпапку, минуя папку «Удаленные элементы».


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Удалить элементы из PST**

Во многих системах обмена сообщениями или почтовых клиентах каждому элементу (например, электронному письму, встрече или заданию) присваивается уникальный идентификатор, называемый идентификатором записи. *delete_item(entry_id)* метод [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс принимает этот идентификатор записи в качестве параметра и удаляет соответствующий элемент из хранилища сообщений. Используйте следующий код для удаления элемента из хранилища сообщений:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Массовое удаление элементов из файла PST**
Aspose.Email API можно использовать для массового удаления элементов из файла PST. Это достигается с помощью метода delete_child_items (), который принимает список элементов Entry ID, относящихся к удаляемым элементам. В следующем фрагменте кода показано, как массово удалять элементы из файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Поиск сообщений и папок в PST по критерию**
Файлы персонального хранилища (PST) могут содержать огромное количество данных, и для поиска данных, соответствующих определенным критериям, в таких больших файлах необходимо включить в код несколько контрольных точек для фильтрации информации. Благодаря классу PersonalStorageQueryBuilder программа Aspose.Email позволяет искать определенные записи в PST на основе заданных критериев поиска. В PST можно искать сообщения на основе таких параметров поиска, как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. PersonalStorageQueryBuilder также можно использовать для поиска подпапок.
### **Поиск сообщений и папок в PST**
В следующем фрагменте кода показано, как использовать класс PersonalStorageQueryBuilder для поиска содержимого в PST на основе различных критериев поиска. Например, показан поиск в PST на основе:

- Важность сообщения.
- Класс сообщений.
- Наличие вложений.
- Размер сообщения.
- Непрочитанные сообщения.
- Непрочитанные сообщения с вложениями и
- папки с определенным именем подпапки.

```py
from aspose.email.mapi import MapiMessageFlags
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder, MapiImportance

with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")
    builder = PersonalStorageQueryBuilder()

    # High importance messages
    builder.importance.equals(2)
    messages = folder.get_contents(builder.get_query())
    print("Messages with High Imp:", messages.count)

    builder = PersonalStorageQueryBuilder()
    builder.message_class.equals("IPM.Note")
    messages = folder.get_contents(builder.get_query())
    print("Messages with IPM.Note:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Messages with attachments AND high importance
    builder.importance.equals(2)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Messages with atts:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Messages with size > 15 KB
    builder.message_size.greater(15000)
    messages = folder.get_contents(builder.get_query())
    print("Messages size > 15 KB:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Unread messages
    builder.has_no_flags(MapiMessageFlags.READ)
    messages = folder.get_contents(builder.get_query())
    print("Unread:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Unread messages with attachments
    builder.has_no_flags(MapiMessageFlags.READ)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Unread msgs with atts:", messages.count)

    # Folder with name 'SubInbox'
    builder = PersonalStorageQueryBuilder()
    builder.folder_name.equals("SubInbox")
    folders = folder.get_sub_folders(builder.get_query())
    print("Folder having subfolder:", folders.count)

    builder = PersonalStorageQueryBuilder()
    # Folders with subfolders
    builder.has_subfolders()
    folders = folder.get_sub_folders(builder.get_query())
    print("Folders with subfolders:", folders.count)
```
### **Поиск строки в PST с параметром Ignore Case**
В следующем фрагменте кода показано, как искать строку в PST с помощью параметра ignore case.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Поиск тем сообщений по нескольким ключевым словам в файле PST**

Извлеките определенные сообщения или элементы из файла персонального хранилища (PST) или хранилища сообщений, внедрив *либо (запрос 1, запрос 2)* метод [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) класс в вашем проекте. Он принимает два параметра, позволяющих объединить два разных запроса, query1 и query2, и найти тему сообщения, соответствующую любому из двух указанных слов. См. пример кода ниже:

```python
import aspose.email as ae

builder1 = ae.storage.pst.PersonalStorageQueryBuilder()
builder1.subject.contains("Review") # 'Review' is key word for the search

builder2 = ae.storage.pst.PersonalStorageQueryBuilder()
builder2.subject.contains("Error") # 'Error' is also key word for the search

builder = ae.storage.pst.PersonalStorageQueryBuilder()
# message subjects must contain 'Review' or 'Error' words
builder.either(builder1.get_query(), builder2.get_query())


pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")
messages = folder.get_contents(builder.get_query())

for message in messages:
    print(f"Message: {message.subject}")
```

## **Переместить элементы в другие папки файла PST**
Aspose.Email позволяет перемещать элементы из исходной папки в другую папку в том же файле личного хранилища (PST). Сюда входят:

- Перемещение указанной папки в новую родительскую папку.
- Перемещение указанных сообщений в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подпапок в новую родительскую папку.

В следующем фрагменте кода показано, как перемещать такие элементы, как сообщения и папки, из исходной папки в другую папку того же файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Обновление свойств сообщения в файле PST**
Иногда требуется обновить некоторые свойства сообщений, такие как смена темы, маркировка важности сообщения и т. д. Обновление сообщения в PST-файле с такими изменениями в свойствах сообщения можно осуществить с помощью метода FolderInfo.change_Messages. В этой статье показано, как массово обновлять сообщения в PST-файле для внесения изменений в свойства. В следующем фрагменте кода показано, как массово обновлять свойства сообщений для нескольких сообщений в PST-файле.

```py
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder
from aspose.email.mapi import MapiPropertyTag, MapiProperty, MapiPropertyCollection

pst_file_path = data_dir + "ya4demia04vb.pst"

# Load the Outlook PST file
with PersonalStorage.from_file(pst_file_path) as personal_storage:
    # Get the required subfolder
    inbox = personal_storage.root_folder.get_sub_folder("Inbox")

    # Find messages having From = "someuser@domain.com"
    query_builder = PersonalStorageQueryBuilder()
    query_builder.from_address.contains("someuser@domain.com")

    # Get contents from query
    messages = inbox.get_contents(query_builder.get_query())

    # Save (MessageInfo, EntryIdString) in a list
    change_list = [message_info.entry_id_string for message_info in messages]

    # Compose the new properties
    updated_properties = MapiPropertyCollection()
    updated_properties.add(
        MapiPropertyTag.SUBJECT_W,
        MapiProperty(MapiPropertyTag.SUBJECT_W, "New Subject".encode("utf-16le"))
    )
    updated_properties.add(
        MapiPropertyTag.IMPORTANCE,
        MapiProperty(MapiPropertyTag.IMPORTANCE, bytearray([0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]))
    )

    # Update messages having From = "someuser@domain.com" with new properties
    inbox.change_messages(change_list, updated_properties)
```
## **Обновление настраиваемых свойств в файле PST**
Иногда требуется пометить элементы, обработанные в файле PST. API Aspose.Email позволяет сделать это с помощью свойств MapiProperty и MapInamedProperty. В этом помогают следующие методы.

- ctor MapInamed Property (длинный тег свойства, идентификатор строкового имени, идентификатор свойства UUID, массив байтов [] Значение свойства)
- ctor MapInamed Property (длинный тег свойств, идентификатор длинного имени, идентификатор свойства UUID, массив байтов [] Значение свойства)
- FolderInfo.change_messages (обновленные свойства коллекции MAPIPropertyCollection) — изменяет все сообщения в папке
- PersonalStorage.change_messages (идентификатор строковой записи, обновленные свойства коллекции свойств MAPI) — изменение свойств сообщения

```py
from uuid import UUID
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import MapiNamedProperty, MapiPropertyCollection
from aspose.email.mapi import MapiPropertyType, MapiProperty, MapiPropertyTag

def generate_named_property_tag(index, data_type):
    return (((0x8000 | index) << 16) | data_type) & 0x00000000FFFFFFFF

def run():
    # Load the Outlook file
    pst_file_path = data_dir + "my.pst"

    with PersonalStorage.from_file(pst_file_path) as personal_storage:
        test_folder = personal_storage.root_folder.get_sub_folder("Inbox")

        # Create the collection of message properties for adding or updating
        new_properties = MapiPropertyCollection()

        # Normal, Custom, and PidLidLogFlags named properties
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

# Usage
run()
```
## **Извлечение вложений без извлечения полного сообщения**
Aspose.Email API можно использовать для извлечения вложений из сообщений PST без предварительного извлечения всего сообщения. Для этого можно использовать метод extract_attachments в IEWSClient. В следующем фрагменте кода показано, как извлекать вложения без извлечения всего сообщения.

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
Ключевые функции Microsoft Outlook — управление электронной почтой, календарями, задачами, контактами и записями журнала. Кроме того, файлы также можно добавлять в папку PST, и полученный PST сохраняет добавленные документы. Aspose.Email предоставляет возможность добавлять файлы в папку таким же образом, а также добавлять сообщения, контакты, задачи и записи журнала в PST. В следующем фрагменте кода показано, как добавлять документы в папку PST с помощью Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}
