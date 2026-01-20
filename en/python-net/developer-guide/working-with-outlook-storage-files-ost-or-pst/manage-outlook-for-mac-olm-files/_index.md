---
title: Managing Outlook OLM Files in Python Applications
ArticleTitle: Managing Outlook for Mac OLM Files
type: docs
weight: 120
url: /python-net/open-read-olm-files-python/
---

OLM (Outlook for Mac Archive) is a file format associated with Microsoft Outlook for Mac. It is used to archive and store email messages, contacts, calendar items, tasks, and other Outlook data on Mac computers. OLM files serve as a backup or archive format, allowing users to save their Outlook for Mac data for future reference or migration. It's important to note that OLM files are specific to Outlook for Mac, and they are not compatible with the PST (Personal Storage Table) file format used by Outlook on Windows. If you need to transfer Outlook data between different platforms, conversion tools will be handy. Aspose.Email offers such tools including opening, reading and other functionalities to work with OLM files.

## **Opening Outlook OLM Files**

OLM format files can be opened in two ways:

- using constructor
- using static 'from_file' method

### **Open Outlook OLM Files Using Python Constructors**

To open a file, call constructor of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class and pass full file name or stream as an argument to it:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
```

### **Open OLM Files Using Python's Static Method FromFile**

To open a file, use static method 'from_file' of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class and pass full file name or stream as an argument to it:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
```

## **Folder and Email Management in OLM Files**

### **Access Folder Structure Recursively**

Aspose.Email API allows you to visualize and display the folder hierarchy retrieved from an OLM file using the *print_all_folders* function. This function takes the *folder_hierarchy* property of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class, along with an indentation level as input, and recursively traverses the hierarchy to print each folder name with the appropriate indentation.

Below is the code sample demonstrating how to use the *print_all_folders* function to display the folder hierarchy from an OLM file:


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

The code sample above is intended to display the folder hierarchy of the OLM file through a recursive function in a more structured and readable format. 

### **Access Folder Structure Directly**

Aspose.Email also makes it possible to directly access the folder structure from the OLM file using the *get_folders()* method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.

Below is a code sample for accessing the folder structure directly:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folders = olm.get_folders()
```

### **Retrieve Folders by Name**

It is possible to retrieve any folder by its name using the *get_folder(name, ignore_case)* method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class. This method requires the folder name and case sensitivity parameters.

Here's a sample code illustrating how to retrieve a folder by its name:


```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)
```

### **List Emails from Outlook OLM Files**

Aspose.Email library can be used to read and extract email messages from Outlook for Mac (OLM) files. You can get the list of emails using the following methods of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class which represents a folder:

- **enumerate_messages()** - Iterates through each email message in the folder. This method returns messages as instances of the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class which provides basic information about each email message, such as subject, sender, date, etc.
- **enumerate_mapi_messages()** - Also iterates through each email message in a folder, but in this case, returns messages as instances of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class which represents an email message in a more detailed and MAPI-specific way. It provides access to a wide range of properties and details of the email message, allowing for more advanced and specialized processing.

The code samples below demonstrate how to extract basic email subjects and save detailed email messages from an Outlook OLM file by using *enumerate_messages()* for subject extraction and *enumerate_mapi_messages()* for saving messages as .msg files.

#### **Extract Basic Email Information Using 'enumerate_messages()' Method**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    print(message_info.subject)
```

#### **Save Detailed Email Messages Using 'enumerate_mapi_messages()' Method**

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for msg in folder.enumerate_mapi_messages():
    msg.save(f"{msg.subject}.msg")
```

### **Retrieve Total Number of Messages in the OLM Folder**

The [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class gives you even more options with the following methods: 

- **has_messages** - Gets a value indicating whether the current folder has messages.
- **message_count** - Gets the message count.

The code sample below demonstrates how to use these methods:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

if folder.has_messages:
   print(f"Message count: {folder.message_count}")
```

### **Get or Set Modified Dates for Outlook OLM Messages**

Aspose.Email makes it possible to retrieve information about the last modification time of an email message. The *modified_date* property of the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class represents the date and time when the message was last modified. 

Here's an example that demonstrates the use of the property:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    modifiedDate = message_info.modified_date
```

## **Extracting OLM Content**

### **Extract Emails from Outlook OLM Files**

You can retrieve the actual MAPI message data from an email storage using the *extract_mapi_message(message_info)* method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class. This method extracts the MAPI message from the storage based on the provided *message_info*.  

The code sample below demonstrates how to use this method:

```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info)
```


### **Extract Outlook Messages from OLM Files by Identifier**

To access MAPI message data, you can use the *entry_id* property to obtain the unique identifier (Entry ID) of a message using the [OlmMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class. Then, you can utilize the *extract_mapi_message(id)* method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class, passing the entry ID as a parameter to retrieve the MAPI message associated with that particular entry ID. The following code snippet demonstrates the use of these features:

```py

import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage.from_file(fileName)
folder = olm.get_folder("Inbox", True)

for message_info in folder.enumerate_messages():
    msg = olm.extract_mapi_message(message_info.entry_id)
```

## **OLM Folder Structure Management**

### **Get Folder Paths in Outlook OLM Files**

Aspose.Email allows you to get hierarchical path or location of the folder within the Outlook OLM file. The API provides the *path* property of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class which returns the folder path. The following code snippet demonstrates the use of this property:

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

## **Count Items in Outlook OLM Folders**

Aspose.Email provides the ability to count the total number of email messages contained within the specific folder of an Outlook OLM file. The *message_count* property of the [OlmFolder](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmfolder/#olmfolder-class) class returns the total items (email messages) count stored within a specific folder in the OLM file. The following code snippet demonstrates the use of this property:

```py
import aspose.email as ae


def print_message_count(folders):
    for folder in folders:
        print(f"Message Count [{folder.name}]: {folder.message_count}")


fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
print_message_count(olm.folder_hierarchy)
```

### **Get the Total Item Count in Outlook OLM Files**

The *get_total_items_count()* method of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class returns the total number of message items contained in the OLM storage as shown in the code sample below:
  
```py
import aspose.email as ae

fileName = "my.olm"
olm = ae.storage.olm.OlmStorage(fileName)
count = olm.get_total_items_count()
```

## **Outlook Category Management**

### **Retrieve Outlook Category Colors**

With Aspose.Email, you can easily retrieve and utilize category colors associated with Outlook item categories stored in OLM files. The [OlmItemCategory](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmitemcategory/) class allows you to access category names and their respective colors represented in hexadecimal format. The [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class features the *GetCategories()* method for retrieving a list of categories from OLM storage. By implementing the code sample below, you can effortlessly retrieve all used categories from an OML storage file and access the category name along with its color. 

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
