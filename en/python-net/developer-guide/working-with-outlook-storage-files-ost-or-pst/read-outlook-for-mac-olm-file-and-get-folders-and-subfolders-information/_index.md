---
title: Read Outlook for Mac OLM File & Get Folders & SubFolders Information
ArticleTitle: Read Outlook for Mac OLM File & Get Folders & SubFolders Information
type: docs
weight: 120
url: /python-net/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
---

OLM (Outlook for Mac Archive) is a file format associated with Microsoft Outlook for Mac. It is used to archive and store email messages, contacts, calendar items, tasks, and other Outlook data on Mac computers. OLM files serve as a backup or archive format, allowing users to save their Outlook for Mac data for future reference or migration. It's important to note that OLM files are specific to Outlook for Mac, and they are not compatible with the PST (Personal Storage Table) file format used by Outlook on Windows. If you need to transfer Outlook data between different platforms, conversion tools will be handy. Aspose.Email offers such tools including opening, reading and other functionalities to work with OLM files.

## **Opening OLM format files**

OLM format files can be opened in two ways:

- using constructor
- using static 'from_file' method

### **Opening files by constructor**

To open a file, call constructor of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class and pass full file name or stream as an argument to it:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Opening files using static method FromFile**

To open a file, use static method 'from_file' of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class and pass full file name or stream as an argument to it:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Getting folders**

You can visualize and display the folder hierarchy retrieved from an OLM file using the 'print_all_folders' function. It takes the 'folder_hierarchy' property of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class and an indentation level as input, then recursively traverses the hierarchy to print each folder name along with appropriate indentation. The code sample below demonstrates how to use this function to display the folder hierarchy from an OLM file. It displays the list of all folders in hierarchical order:

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

The code sample above is intended to display the folder hierarchy of the OLM file through a recursive function in a more structured and readable format. Aspose.Email also makes it possible to directly accesses the folder structure from the OLM file using the 'get_folders()' method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

Also, it's possible to get any folder by name. The following code sample utilizes the 'get_folder(name, ignore_case)' method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class passing the folder name and the case sensitivity as parameters to retrieve the folder by its name:


```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

## **List of emails**

The code snippets below demonstrate how to use the Aspose.Email library to read and extract email subjects from an Outlook for Mac (OLM) file. [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class, which represents a folder, has the following methods to get the list of emails:

- 'enumerate_messages()' - Iterates through each email message in the folder. This method returns messages as instances of the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class which provides basic information about each email message, such as subject, sender, date, etc.
- 'enumerate_mapi_messages()' - Also iterates through each email message in a folder, but in this case, returns messages as instances of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class which represents an email message in a more detailed and MAPI-specific way. It provides access to a wide range of properties and details of the email message, allowing for more advanced and specialized processing.

### **Using EnumerateMessages method**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    print(message_info.subject)
```

### **Using EnumerateMapiMessages method**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for msg in folder.enumerate_mapi_messages():
    msg.save(f"{msg.subject}.msg")
```

### **Other useful properties**

The other useful properties of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class are: 

- 'has_messages' - Gets a value indicating whether the current folder has messages.
- 'message_count' - Gets the message count.

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Message count: {folder.message_count}")
```

### **Get or Set the Modified Date of a Message**

You can retrieve information about the last modification time of an email message. The 'modified_date' property of the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class represents the date and time when the message was last modified. 

Here's an example that demonstrates the use of the property:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Extracting emails**

You can retrieve the actual MAPI message data from an email storage.The 'extract_mapi_message(message_info)' method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class is used to extract the MAPI message from the storage based on the provided message_info.  

The code sample below demonstrates how to use this method:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
```

## **Extracting all Items from an Email using Traversal API**

You can extract all items from an Outlook OLM file as far as possible, without throwing out exceptions, even if some data of the original file is corrupted. To perform this, use [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) constructor and [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method instead of FromFile method. The constructor allows defining a callback method.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
```
The callback method makes loading and traversal exceptions available.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```cs
if (olm.Load(fileName))
```

The following code snippet and the steps show how to use this API:

1. Create a new instance of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class, passing an exception handling callback to handle any exceptions encountered during the process.
2. Load the OLM file by calling the [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method of the OlmStorage instance. 
3. If the OLM file is successfully loaded, obtain the folder hierarchy by calling the [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) method on the OlmStorage instance. This returns a list of OlmFolder objects.
4. Call the ExtractItems method, passing the OlmStorage instance and the list of OlmFolder objects.
5. In the ExtractItems method, iterate through each folder in the folders list.
6. If the folder contains messages (emails), print the folder name to the console using Console.WriteLine(folder).
7. Iterate through the messages in the current folder by calling the EnumerateMessages method on the OlmStorage instance, passing the current folder as an argument.
8. Print the subject of each message to the console using Console.WriteLine(msg.Subject).
9. If the folder has subfolders, recursively call the ExtractItems method again, passing the OlmStorage instance and the subfolders of the current folder.

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
## **Extract Messages from OLM by Identifiers**

To access MAPI message data, you can use the 'entry_id' property to obtain the unique identifier (Entry ID) of a message using the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class. Then, you can utilize the 'extract_mapi_message(id)' method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class, passing the entry ID as a parameter to retrieve the MAPI message associated with that particular entry ID. The following code snippet demonstrates the use of these features:

```py

import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **Get Folder Path**

You may also get hierarchical path or location of the folder within the Outlook OLM file. Aspose.Email provides the 'path' property of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class which returns the folder path. The following code snippet demonstrates the use of this property:

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

## **Count the Number of Items in the Folder**

Aspose.Email provides the ability to count the total number of email messages contained within the specific folder of an Outlook OLM file. The 'message_count' property of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class returns the total items (email messages) count stored within a specific folder in the OLM file. The following code snippet demonstrates the use of this property:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Message Count [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Get Total Items Count of OlmStorage**

The 'get_total_items_count()' method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class returns the total number of message items contained in the OLM storage.
  
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Retrieve Outlook Category Colours**

With Aspose.Email, you can easily retrieve and utilize category colors associated with Outlook item categories stored in OLM files. The [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) class allows you to access category names and their respective colors represented in hexadecimal format. The [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class features the 'GetCategories()' method for retrieving a list of categories from OLM storage. By implementing the code sample below, you can effortlessly retrieve all used categories from an OML storage file and access the category name along with its color. 

```py
with OlmStorage.FromFile("storage.olm") as olm:
    categories = olm.GetCategories()
    
    for category in categories:
        print(f"Category name: {category.Name}")
        
        # Color is represented as a hexadecimal value: #rrggbb
        print(f"Category color: {category.Color}")
```

Additionally, you can retrieve the category color associated with specific messages by iterating through the messages in a folder and accessing the corresponding category color based on the category name.

```py
for msg in olm.EnumerateMessages(folder):
    if msg.Categories is not None:
        for msgCategory in msg.Categories:
            print(f"Category name: {msgCategory}")
            categoryColor = next((c.Color for c in categories if c.Name.lower() == msgCategory.lower()), None)
            if categoryColor is not None:
                print(f"Category color: {categoryColor}")
```
