---
title: Working with Messages in a PST File
ArticleTitle: Working with Messages in a PST File
type: docs
weight: 100
url: /python-net/working-with-messages-in-a-pst-file/
---


## **Adding Messages to PST Files**
Create a New PST File and Add Subfolders showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add messages to subfolders of a PST file that you have created or loaded. This article adds two messages from disk to the Inbox subfolder of a PST. Use the PersonalStorage and FolderInfo classes to add messages to PST files. To add messages to a PST file's Inbox folder:

1. Create an instance of the FolderInfo class and load it with the contents of the Inbox folder.
1. Add messages from disk to the Inbox folder by calling the FolderInfo.add_message() method. The FolderInfo class exposes the add_messages method that enables to add large number of messages to the folder, reducing I/O operations to disc and improving performance. A complete example can be found below, in Adding Bulk Messages.

The code snippets below shows how to add messages to a PST subfolder called Inbox.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Adding Bulk Messages**
Adding individual messages to a PST implies more I/O operations to disc and hence may slow down performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. The add_messages method allows you to define a range of message be added to the PST for improved performance and can be used as in the following scenarios.
### **Loading Messages from Disc**
The following code snippet shows you how to loading messages from disc.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Usage
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **MapiMessageCollection Implementation**
The following code snippet shows you how to implement MapiMessageCollection.

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
### **Adding Messages from Other PST**
For adding messages from the another PST, use the FolderInfo.enumerate_mapi_messages() method. The following code snippet shows you how to add messages from other PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Get Messages Information from an Outlook PST File**
In Read Outlook PST File and Get Folders and Subfolders Information, we discussed loading an Outlook PST file and browse its folders to get the folder names and the number of messages in them. This article explains how to read all the folders and subfolders in the PST file and display the information about messages, for example, subject, sender, and recipients. The Outlook PST file may contain nested folders. To get message information from these, as well as the top-level folders, use a recursive method to read all the folders. The following code snippet shows you how to reads an Outlook PST file and display the folder and message contents recursively.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Extracting Messages Form PST Files**

This article shows how to read Microsoft Outlook PST files and extract messages. Below is a code snippet showing how to extract messages from a PST file.

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
### **Extracting n Number of Messages from a PST File**

To extract a specific number of messages from a PST file, use the *get_contents(start_index, count)* method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class. It takes two parameters:

- **start_index** - the number of the starting message, for example the 10th;
- **count** - total number of messages to retrieve.

Retrieving only the necessary subset of messages at a time can be useful for managing large volumes of email data. The following code sample demonstrates the implementation of this feature:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Extracts messages starting from 10th index top and extract total 100 messages
messages = folder.get_contents(10, 100)
```
### **Getting Total Items Count from a PST File**

To retrieve the total number of items (such as emails, appointments, tasks, contacts, etc.) present in the message store, use the *get_total_items_count()* method of the [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) class. It provides a convenient way to quickly gather information about the size and volume of data within the store. The following code snippet shows how to get the total number of items from a PST file:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Delete Messages from PST Files**
Add Messages to PST Files showed how to add messages to PST files. It is, of course, also possible to delete items (contents) from a PST file and it may also be desirable to delete messages in bulk. Items from a PST file can be deleted using the FolderInfo.delete_child_item() method. The API also provides FolderInfo.delete_child_items() method to delete items in bulk from the PST file.
### **Deleting Messages from PST Files**
This articles shows how to Use the FolderInfo class to access specific folders in a PST file. To delete messages from the Sent subfolder of a previously loaded or created PST file:

1. Create an instance of the FolderInfo class and load it with the contents of the sent subfolder.
1. Delete messages from the Sent folder by calling the FolderInfo.delete_child_item() method and passing the MessageInfo.entry_id as a parameter. The following code snippet shows you how to delete messages from a PST file's Sent subfolder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Deleting Folders from PST Files**

You can delete a PST folder by moving it to the Deleted Items folder.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Empty folder")
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
The advantage of this method is that the deleted folder can be easily recovered.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```
You can also permanently remove a folder from the Deleted Items folder, if necessary.


```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
The *delete_child_item* method can be used for any folders if you want to immediately and permanently delete a subfolder, bypassing the Deleted Items folder.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Delete Items from PST**

In many messaging systems or email clients, each item (such as an email, appointment, or task) is assigned a unique identifier called an entry ID. The *delete_item(entry_id)* method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class takes this entry ID as a parameter and removes the corresponding item from the message store. Use the following code to delete an item from the message store:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Delete Items in Bulk from PST File**
Aspose.Email API can be used to delete items in bulk from a PST file. This is achieved using the delete_child_items() method which accepts a list of Entry ID items referring to the items to be deleted. The following code snippet shows you how to delete Items in bulk from PST file.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Search Messages and Folders in a PST by Criterion**
Personal Storage (PST) files can contain a huge amount of data and searching for data that meets a specific criteria in such large files needs to include multiple check points in the code to filter the information. With the PersonalStorageQueryBuilder class, Aspose.Email makes it possible to search for specific records in a PST based on a specified search criteria. A PST can be searched for messages based on search parameters such as sender, receiver, subject, message importance, presence of attachments, message size, and even message ID. The PersonalStorageQueryBuilder can also be used to search for subfolders.
### **Searching Messages and Folders in PST**
The following code snippet shows you how to use the PersonalStorageQueryBuilder class to search for contents in a PST based on different search criteria. For example, it shows searching a PST based on:

- Message importance.
- Message class.
- Presence of attachments.
- Message size.
- Unread messages.
- Unread messages with attachments, and
- folders with specific subfolder name.

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
### **Searching for a String in PST with the Ignore Case Parameter**
The following code snippet shows you how to search for a string in PST with the ignore case parameter.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Searching for Message Subjects by Multiple Keywords in a PST File**

Retrieve specific messages or items from a personal storage file (PST) or message store by implementing the *either(query1, query2)* method of the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) class in your project. It takes two parameters allowing you to combine two different queries, query1 and query2, and find a message subject matching either of the two specified words. See the code sample below:

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

## **Move Items to Other Folders of PST File**
Aspose.Email makes it possible to move items from a source folder to another folder in the same Personal Storage (PST) file. This includes:

- Moving a specified folder to a new parent folder.
- Moving a specified messages to a new folder.
- Moving the contents to a new folder.
- Moving subfolders to a new parent folder.

The following code snippet shows you how to move items such as messages and folders from a source folder to another folder in the same PST file.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Updating Message Properties in a PST File**
It's sometimes required to update certain properties of messages such as changing the subject, marking message importance and similarly others. Updating a message in a PST file, with such changes in the message properties, can be achieved using the FolderInfo.change_messages method. This article shows how to update messages in bulk in a PST file for changes in the properties. The following code snippet shows you how to update properties of messages in bulk mode for multiple messages in a PST file.

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
## **Updating Custom Properites in a PST File**
Sometimes its required to mark items that are processed with in the PST file. Aspose.Email API allows to achieve this using the MapiProperty and MapiNamedProperty. The following methods are helpful in achieving this.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- FolderInfo.change_messages(MapiPropertyCollection updatedProperties) - changes all messages in folder
- PersonalStorage.change_messages(string entryId, MapiPropertyCollection updatedProperties) - change message properties

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
## **Extract Attachments without Extracting Complete Message**
Aspose.Email API can be used to extract attachments from PST messages without extracting the complete message first. The extract_attachments method of IEWSClient can be used to do this. The following code snippet shows you how to extract attachments without extracting complete message.

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
## **Adding Files to PST**
Microsoft Outlook's key functionality is managing emails, calendars, tasks, contacts and journal entries. In addition, files can also be added to a PST folder and the resulting PST keeps record of the documents added. Aspose.Email provides the facility to add files to a folder in the same way in addition to adding messages, contacts, tasks and journal entries to PST. The following code snippet shows you how to add documents to a PST folder using Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}
