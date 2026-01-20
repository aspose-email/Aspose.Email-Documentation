---
title: Convert OLM to PST
ArticleTitle: Convert OLM to PST
type: docs
weight: 90
url: /python-net/convert-olm-to-pst/
---


## **Convert OLM to PST** 

OLM (Outlook for Mac) is a file format used by Microsoft Outlook for Mac to store email messages, contacts, calendars, tasks, and other data. It is the native file format for Outlook for Mac, so it is not possible to open an Outlook for Mac (OLM) file in Outlook for Windows. To work with OLM files in Windows, Aspose Email provides tools specifically designed to handle OLM files. Its approach is to convert OLM files to PST (Outlook Data File) format, which is widely supported in Windows environments. Once converted to PST format, you can then import the data into Outlook for Windows or any other compatible email client. 

### **Primary Approach**

The following code sample demonstrates how to convert an Outlook OLM file to a PST file using the Aspose.Email library. It reads each folder and the corresponding messages from the OLM file and adds them to the new PST file in the same order. 

1. Create an instance of the [OlmStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class to open the source OLM file.
2. Use the [PersonalStorage.create](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method to create a new PST file with a specified filename and format version.
3. Recursively read each folder and its messages from the OLM file.
4. Use the **add_to_pst** function to add each folder and its messages to the PST file, maintaining the original structure.

```py

import aspose.email as ae

olm = ae.storage.olm.OlmStorage("my.olm")

pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```

This code is the main script for initiating the process of converting an OLM file to a PST file using the aspose.email library. It demonstrates how to open an OLM file, create a new PST file, and call the **add_to_pst** function to perform the data transfer task. This script serves as the entry point for the migration, efficiently using the function to handle the detailed transfer of folders and messages.

### **Recursive Folder and Message Transfer**

This approach provides a deeper control over the folder and message handling process while migrating email data from an OLM file to a PST file. The code sample below utilizes the **add_to_pst** function which defines the transfer logic. Its primary role is to recursively traverse through folders and messages, ensuring they are properly transferred and replicated in the PST format. This function is highly reusable and expects to be used as part of a larger application or script that manages the opening and creation of these files.

```py

def add_to_pst(pst_folder, olm_folder):
    pst_sub_folder = pst_folder.get_sub_folder(olm_folder.name)

    for msg in olm_folder.enumerate_mapi_messages():
        if pst_sub_folder is None:
            pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name, get_container_class(msg.message_class))

        pst_sub_folder.add_message(msg)

    if pst_sub_folder is None:
        pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name)

    for olm_sub_folder in olm_folder.sub_folders:
        add_to_pst(pst_sub_folder, olm_sub_folder)
```

### **Determine Folder Types in PST**

When converting an OLM file to PST, we must ensure that the folder structure is preserved and that each folder in the PST file has the correct type. Unlike PST, folders in OLM do not have predefined types. To correctly categorize and transfer data, follow the steps below:

1. Read the first message from an OLM folder and determine its type.
2. Use this message type to calculate the appropriate folder type in PST using a classification method.
3. Create a folder of the determined type in the PST file.
4. Add the message to the newly created PST folder.

For the remaining messages in the OLM folder, we assume they belong to the same category, as the folder type has already been established.

The **get_container_class** function helps categorize Outlook items by mapping different message classes to the correct PST folder types:


```py
def get_container_class(message_class):
    if message_class.startswith("IPM.Contact") or message_class.startswith("IPM.DistList"):
        return "IPF.Contact"

    if message_class.startswith("IPM.StickyNote"):
        return "IPF.StickyNote"

    if message_class.startswith("IPM.Activity"):
        return "IPF.Journal"

    if message_class.startswith("IPM.Task"):
        return "IPF.Task"

    if message_class.startswith("IPM.Appointment") or message_class.startswith("IPM.Schedule.meeting"):
        return "IPF.Appointment"

    return "IPF.Note"
```
