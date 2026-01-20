---
title: Create and Organize PST Files in Python
ArticleTitle: Create and Organize PST Files in Python
type: docs
weight: 10
url: /python-net/create-new-pst-file-and-add-subfolders/
---

## **Create New PST File and Add Subfolders**

Aspose.Email provides the functionality to create Personal Storage Table (PST) files from scratch and add subfolders to them. With the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/) class, you can manage operations related to PST files, which store email messages, calendar events, contacts, and other data.

The following code sample demonstrates how to create a new storage file and add an "Inbox" folder to it:

1. Use the [PersonalStorage.create](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method to generate a new PST file with the specified directory. The file is created using the `UNICODE` format for compatibility with modern applications.
2. Access the root folder of the PST file and add a new subfolder named "Inbox" to organize email messages.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}

### **Container Class Matching Check**

Aspose.Email for Python offers a solution that enhances the validation process during folder creation in PST files. With the *enforce_container_class_matching* property of the [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) class, you can ensure strict matching of container classes when adding a new folder to the PST storage. This feature helps maintain the organizational hierarchy within the PST file by preventing mismatches in container classes. By setting 'EnforceContainerClassMatching' to 'true', an exception will be thrown if the container classes of the parent and child folders do not match, providing a safeguard against incorrect folder structures. The default behavior of this property is 'false', allowing flexibility in folder creation while enabling you to enforce strict container class matching when required. 

The following code sample demonstrates the use of the *enforce_container_class_matching* property to control whether an exception should be thrown when adding folders with mismatching container classes:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
    
    # An exception will not arise. EnforceContainerClassMatching is False by default.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
    
    # An exception will occur as the container class of the subfolder being added (IPF.Note)
    # does not match the container class of the parent folder (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Changing Folder Container Class**

Sometimes it is necessary to change a folder class. A common example is where messages of different types (appointments, messages, etc.) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code snippet shows you how to change the container class of a folder in PST for this purpose:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}

## **Add Bulk Messages with Improved Performance**

Adding bulk messages to a PST file as opposed to adding them individually can offer several advantages, particularly in terms of efficiency and performance: less I/O operations, reduced time to complete the task, system resources are more effeciently utilized, etc. The *add_messages* method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class is used to transfer the collection of MAPI messages obtained from the source folder to the destination folder.

### **Add Messages from Another PST**

To enumerate and retrieve all the MAPI messages from the source folder of a PST file, use the *enumerate_mapi_messages()* method of the [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class. Then, add these messages to the destination folder of another PST file.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Get the folder by name
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Add Messages from Directory**

To add messages from directory, after the file is opened and the reference to a specific folder within the PST file is obtained, retrieve a list of file names from a directory specified by the "path" variable and create an empty MSG list to load each file as a MapiMessage. Append each loaded message to the *msg_list*. The code sample below demonstrates the process of adding messages from directory:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Get the folder by name
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```
