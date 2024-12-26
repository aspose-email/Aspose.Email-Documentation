---
title: Reading corrupted PST/OST files
ArticleTitle: Reading corrupted PST/OST files
type: docs
weight: 90
url: /python-net/reading-corrupted-pst-ost-files/
---


## **Reading corrupted PST/OST files**

Sometimes it may not be possible to open a PST file due to some issues. One of those issues is the file corruption. If a PST file is corrupted or damaged, it may not be possible to open the file using Outlook email client. Aspose.Email provides API designed to scan a damaged PST file and read the undamaged messages within a file by their IDs.

The following methods of the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class are essential to cope with these tasks: 

To get the list of IDs:

- **find_messages(parent_entry_id)** - retrieves a list of message IDs within a specified folder.

- **find_subfolders(parent_entry_id)** - obtains a list of subfolder IDs within the root folder.

To use these IDs to get the contents of the file:

- **extract_message(entry_id)** - attempts to retrieve a message.

- **get_folder_by_id(entry_id)** - accesses each folder.

The following code sample demonstrates how to explore and access the contents of a potentially corrupted PST file:

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
