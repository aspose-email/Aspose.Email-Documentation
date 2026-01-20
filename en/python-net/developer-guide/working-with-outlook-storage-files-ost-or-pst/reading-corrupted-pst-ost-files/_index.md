---
title: Reading corrupted PST/OST files
ArticleTitle: Reading corrupted PST/OST files
type: docs
weight: 90
url: /python-net/read-corrupted-pst-ost-files/
---


## **Reading Corrupted PST/OST Files**

In some cases, a PST or OST file may become inaccessible due to corruption or damage. When this happens, Outlook may fail to open the file, making it difficult to retrieve important emails and other mailbox data.

Aspose.Email provides an API that allows you to scan and extract undamaged messages from a corrupted PST file using message and folder IDs.

The following methods of the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class are essential for recovering data from a corrupted PST file:

- Retrieve Message and Folder IDs:

    **find_messages(parent_entry_id)** - retrieves a list of message IDs within a specified folder.

    **find_subfolders(parent_entry_id)** - obtains a list of subfolder IDs within a given folder.

- Access Messages and Folders Using Their IDs:

    **extract_message(entry_id)** - extracts a message from the PST file using its entry ID.

    **get_folder_by_id(entry_id)** - retrieves a folder from the PST file using its entry ID.


The following code sample demonstrates how to navigate through a potentially corrupted PST file, extract undamaged messages, and explore subfolders:


```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Message reading error. Entry id: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Message reading error. Entry id: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```
