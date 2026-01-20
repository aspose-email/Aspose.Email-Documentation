---
title: Working with Messages in a PST File
ArticleTitle: Working with Messages in a PST File
type: docs
weight: 100
url: /python-net/working-with-messages-in-a-pst-file/
---


## **Add Messages to Outlook PST Files**

### **Add a Single Message to a PST File**

[Create a New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) shows how to create a PST file and add a subfolder to it. With Aspose.Email you can also add messages to subfolders of a PST file that you have created or loaded. The code sample below demonstrates how to create a new PST file, add an "Inbox" folder, and then add a message to that folder. The [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) and the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) classes are used to perform the task.

1. Use the [PersonalStorage.create](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method to initiate a new PST file specifying the file path and the file format version as Unicode.
2. Create a new folder named "Inbox" in the root directory of the PST file.
3. Add a message to the newly created "Inbox" folder using the [add_message](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method.
4. Load the message using [MapiMessage.load](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods).


```py
pst = PersonalStorage.create(dataDir + "AddMessagesToPst_out.pst", FileFormatVersion.UNICODE)

# Add new folder "Inbox"
inboxFolder = pst.root_folder.add_sub_folder("Inbox");

# Add message to Inbox Folder
inboxFolder.add_message(MapiMessage.load(dataDir + "MapiMsgWithPoll.msg"))

pst.dispose()
```

## **Add Multiple Messages to PST Files for Better Performance**

Adding individual messages to a PST implies more I/O operations to disc and hence may slow down performance. To improve performance, messages can be added to PST in bulk mode, and minimize I/O operations.

### **Load and Add Messages from Disk**

The [add_messages](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method allows you to define a range of messages to be added to a PST file. The code sample below demonstrates how to add multiple messages from disk to a PST file for improved performance: 

1. Define a function by creating `add_messages_in_bulk_mode` with parameters for the PST filename and the folder with messages.
2. Open the specified PST file using [PersonalStorage.from_file()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods).
3. Retrieve subfolder "myInbox" from the PST root folder.
4. Add messages from the specified folder in bulk using [folder.add_messages()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods).
5. Call `add_messages_in_bulk_mode()` with the PST file and folder name as arguments.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion

def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Add multiple messages from the specified folder to the PST file for improved performance
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```

### **Use `MapiMessageEnumerator` for Bulk Operations**

To streamline bulk message processing, you can implement the `MapiMessageEnumerator` class which efficiently iterates through messages stored in a specified folder. The following Python script provides a structured approach to enumerating and iterating over MAPI messages using the Aspose.Email library. It defines two helper classes:

- `MapiMessageEnumerator` for reading messages from a directory,

- and `MapiMessageCollection` for managing them during batch operations.

This approach facilitates the traversal and handling of MAPI message files.

```py
import os
from aspose.email.mapi import MapiMessage

# Define a class to enumerate through MAPI message files in a directory
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

# Define a collection class for managing MAPI messages
class MapiMessageCollection:
    def __init__(self, path):
        self.path = path

    def __iter__(self):
        return MapiMessageEnumerator(self.path)


# Iterate through MAPI messages in a specific directory
msg_folder_name = "\\Files\\msg"

# Initialize a collection with the directory containing message files
message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Process each MAPI message object as needed
    pass
```

### **Add Messages from Another PST**

To import messages from one PST file to another, Aspose.Email provides the [FolderInfo.enumerate_mapi_messages()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method. The following code sample demonstrates how to copy messages from an "Inbox" folder in one PST file to another PST file:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}

## **Retrieve Messages from Outlook PST Files**

In [Read Outlook PST Files, Retrieve Folders and SubFolders Information](https://docs.aspose.com/email/python-net/read-outlook-pst-files-python), we discussed loading an Outlook PST file and browse its folders to get the folder names and the number of messages in them. This article explains how to access and extract messages from Outlook PST files: retrieve basic message details, count the number of items in a folder, and extract a specific number of messages for processing or analysis. 

### **Retrieve Basic Message Information**

The code sample below demonstrates how to extract and display key information from MAPI messages stored in a PST file using the Aspose.Email library. It initializes a [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/) object from an "Outlook.pst" file, retrieves the contents of the root folder, and iterates through each message. The script prints details such as the subject, sender information, recipient addresses, delivery time, and message body, providing a comprehensive overview of each email in the specified PST file.

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

### **Recursive Reading of Nested Folders**

An Outlook PST file may contain nested folders. To get message information from these, as well as the top-level folders, use a recursive method to read all the folders. The following code snippet shows you how to read an Outlook PST file and display the folder and message contents recursively:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}

### **Retrieve the Total Number of Items in a PST Folder**

To retrieve the total number of items (such as emails, appointments, tasks, contacts, etc.) present in the message store, use the *get_total_items_count()* method of the [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) class. It provides a convenient way to quickly gather information about the size and volume of data within the store. The following code snippet shows how to get the total number of items from a PST file:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

### **Extract a Specific Number of Messages**

To extract a specified number of messages from a PST file, use the *get_contents(start_index, count)* method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class. It takes two parameters:

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

## **Work with Attachments in PST Files**

### **Extract Attachments without Extracting Entire Messages**

Aspose.Email for Python allows extracting attachments from PST messages without the need to first extract the entire message. This can be done using the [extract_attachments](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method of the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class. The following code snippet demonstrates how to extract attachments while skipping .msg files:

```py
from aspose.email.storage.pst import PersonalStorage

# Open the PST file 
with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    # Get the "Inbox" subfolder from the root folder in the personal storage
    folder = personal_storage.root_folder.get_sub_folder("Inbox")

    # Iterate over each message entry ID in the Inbox folder
    for message_info in folder.enumerate_messages_entry_id():
        # Extract attachments for the current message
        attachments = personal_storage.extract_attachments(message_info)

        # Check if the message has any attachments
        if attachments.count > 0:
            # Iterate over each attachment in the list
            for attachment in attachments:
                # Ignore attachments that are message files (.msg)
                if attachment.long_file_name and attachment.long_file_name.endswith(".msg"):
                    continue
                # Save the attachment with its original file name
                attachment.save(data_dir + attachment.long_file_name)
```

## **Add Files as Attachments to PST Messages**

Microsoft Outlook is a powerful tool for managing emails, calendars, tasks, contacts, and journal entries. Beyond these core functionalities, it also allows for the addition of files to PST folders, enabling users to keep a comprehensive record of associated documents. Aspose.Email simplifies the process of adding files to a PST folder, functioning similarly to how it handles messages, contacts, tasks, and journal entries.

The following code snippet illustrates how to add a document to a PST folder with Aspose.Email:


```py
from aspose.email.storage.pst import PersonalStorage, FileFormatVersion

# Create a new PST file
personal_storage = PersonalStorage.create(data_dir + "AddFilesToPst_out.pst", FileFormatVersion.UNICODE)

# Add a new folder to store files
folder = personal_storage.root_folder.add_sub_folder("Files")

# Add a file to the PST folder
folder.add_file(data_dir + "FileToBeAddedToPST.txt", "")
```

## **Search and Filter Messages in PST Files**

Personal Storage (PST) files can contain a large amount of data, and it requires incorporating multiple filtration to find data matching specific criteria. With the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/) class, Aspose.Email enables you to search for specific records in a PST based on defined search criteria. You can search for messages using parameters such as sender, recipient, subject, message importance, presence of attachments, message size, and even message ID. Additionally, the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/) can be used for searching within subfolders. The following sections provide a comprehensive guide on searching Outlook PST files. 


### **Search Outlook Messages and Folders**

The following code snippet shows you how to use the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/) class to search for contents in a PST based on different search criteria. It particularly demonstrates searching a PST based on:

- Message importance.
- Message class.
- Presence of attachments.
- Message size.
- Unread messages.
- Unread messages with attachments, and
folders with specific subfolder name.

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

### **Search with Case-Insensitive Matching**

By utilizing Aspose.Email [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/), you can specify search conditions for email messages while ignoring case sensitivity, enabling a more flexible and user-friendly search experience. The following code sample demonstrates how to load a PST file, access the "Inbox" folder, and apply case-insensitive search filters to locate emails based on sender information. This feature is especially helpful when dealing with varied capitalization in email data.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Search Subject Lines Using Multiple Keywords**

Retrieve specific messages or items from a personal storage file (PST) or message store by implementing the `either(query1, query2)` method of the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) class. It takes two parameters allowing you to combine two different queries, query1 and query2, and find a message subject matching either of the two specified words. See the code sample below:

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

### **Filter Emails in PST on Specific Criteria**

Retrieve only the messages that match a specific filter, such as subject, sender, or date, using the [MailQuery](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquery/) class. The following code sample demonstrates how to use the Aspose.Email library to load a PST file and filter messages within a specific folder, in this case, the "Inbox" folder:

```py
import aspose.email as ae

# Load the PST file and access a folder
pst = ae.PersonalStorage.from_file("sample.pst")
inbox = pst.root_folder.get_sub_folder("Inbox")

# Create a MailQuery to filter messages by subject
query_builder = ae.MailQueryBuilder()
query_builder.subject.contains("Invoice")

query = query_builder.get_query()

# Enumerate filtered messages
for info in inbox.enumerate_mapi_messages(query):
    print("Subject:", info.subject)
```

### **Retrieve Messages by Type**

The Aspose.Email [MessageKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagekind/#messagekind-enumeration) overload allows you to get messages of a specific type, such as only emails, appointments, or contacts. The following code sample demonstrates how to access and filter specific types of messages from a designated folder:

```py
import aspose.email as ae

# Load the PST and target folder
pst = ae.PersonalStorage.from_file("sample.pst")
inbox = pst.root_folder.get_sub_folder("Inbox")

# Retrieve only email messages (not calendar items, contacts, etc.)
for info in inbox.enumerate_mapi_messages(ae.MessageKind.MAPI_MESSAGE):
    print("Email Message:", info.subject)
```

### **Paginate Message Retrieval for Large PST Files**

When working with folders containing a large number of messages, you can use pagination to load messages in chunks using the `start_index` and `count` parameters. The following code sample demonstrates how to access and retrieve a specific range of email messages from a PST file rather than all of them at once:


```python
import aspose.email as ae

# Load the PST and access the target folder
pst = ae.PersonalStorage.from_file("sample.pst")
inbox = pst.root_folder.get_sub_folder("Inbox")

# Retrieve messages from index 0 to 9
for info in inbox.enumerate_mapi_messages(0, 10):
    print("Paged Message:", info.subject)
```

## **Update and Organize Outlook PST Content**

### **Move Messages between Folders**

Aspose.Email makes it possible to move items from a source folder to another folder in the same Personal Storage (PST) file. This includes:

- Moving a specified folder to a new parent folder.
- Moving a specified messages to a new folder.
- Moving the contents to a new folder.
- Moving subfolders to a new parent folder.

The following code snippet shows you how to move items such as messages and folders from a source folder to another folder in the same PST file.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}

### **Update Message Properties**

It's sometimes required to modify certain properties of messages such as changing the subject, marking message importance and more. Updating these properties within a PST file can be achieved by using the [FolderInfo.change_messages](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method provided by Aspose.Email for Python. This article showcases the process of bulk updating message properties, allowing for automated adjustments across multiple messages within a PST file. Below there is a code snippet illustrating how to perform bulk updates on various message properties.


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

### **Modify Custom MAPI Properties**

Sometimes you may need to identify and mark items that have been processed within a PST file. The Aspose.Email API offers a solution for this task through the use of [MapiProperty](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiproperty/) and [MapiNamedProperty](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinamedproperty/) classes. These classes enable you to label processed items by assigning custom properties to them. Below, you will find methods that are particularly useful for accomplishing this marking process:

- [MapiNamedProperty(long propertyTag, string nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinamedproperty/#constructors)
- [MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinamedproperty/#constructors)
- [FolderInfo.change_messages(MapiPropertyCollection updatedProperties)](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) - changes all messages in a folder
- [PersonalStorage.change_message(string entryId, MapiPropertyCollection updatedProperties)](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) - changes message properties

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

## **Delete Messages and Folders from Outlook PST Files**

Managing the content of Outlook PST files often involves removing unnecessary messages, folders, or multiple items at once. Aspose.Email for Python via .NET provides efficient methods to delete messages and folders from a PST file, whether you need to remove individual emails, [FolderInfo.delete_child_item()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method, or perform bulk deletions, [FolderInfo.delete_child_items()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method, for better file management.

### **Delete Messages from PST Files**

Aspose.Email provides the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class to access specific folders in a PST file. The code sample below demonstrates how to use this class for accessing and deleting messages from the Sent subfolder of a previously loaded or created PST files. Specifically, it retrieves the message count and deletes the first item in the "Sent Items" folder.

1. A PST object is initialized  by opening the "Outlook.pst" file located in the specified directory using [PersonalStorage.from_file()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods).
2. The Sent Items folder is accessed using [pst.get_predefined_folder(StandardIpmFolder.SENT_ITEMS)](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods).
3. Then, the code retrieves the contents of the "Sent Items" folder with [folder.get_contents()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods), counts them, and prints the total number of messages in this folder.
4. The code accesses the first message in the "Sent Items" folder with *msgsColl[0]* and deletes it using [folder.delete_child_item(msgInfo.entry_id)](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods). This function uses the entry ID of the message to remove it from the folder.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

After deletion, the code again counts the messages in the "Sent Items" folder and prints the updated count.

### **Delete Items from PST Files**

In many messaging systems or email clients, each item (such as an email, appointment, or task) is assigned a unique identifier called an entry ID. The `delete_item(entry_id)` method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class takes this entry ID as a parameter and removes the corresponding item from the message store. Use the following code to delete an item from the message store:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

pst.delete_item(entry_id)
```

### **Delete Items in Bulk**

Aspose.Email API can be used to delete items in bulk from a PST file. This is achieved using the `delete_child_items()` method which accepts a list of Entry ID items referring to the items to be deleted. The following code snippet shows you how to delete Items in bulk from a PST file.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}

### **Delete Folders from PST Files**

Outlook PST files may contain folders that are no longer needed. Aspose.Email for Python via .NET allows you to delete these folders either by moving them to the Deleted Items folder (making them recoverable) or by permanently removing them. The following examples demonstrate both approaches.

#### **Move a Folder to Deleted Items (Soft Delete)**

The `move_item` method of the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class allows folders to be recovered later, as they are not permanently removed but moved to the Deleted Items folder. The following code snippet shows how to implement this method into a python project:

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

#### **Restore a Folder from Deleted Items**

The [move_item](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method allows you to restore a folder, if it was mistakenly deleted, by moving it back from Deleted Items to its original location.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```

#### **Permanently Delete a Folder from Deleted Items**

The `delete_child_item` method can be used for any folders if you want to immediately and permanently delete a subfolder, bypassing the Deleted Items folder. The following code sample shows how to remove the folder completely from Deleted Items, making recovery impossible:

```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```

#### **Permanently Delete a Folder Immediately**

If a folder should be deleted without moving it to Deleted Items, the `delete_child_item` method ensures immediate and permanent removal.

```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```



