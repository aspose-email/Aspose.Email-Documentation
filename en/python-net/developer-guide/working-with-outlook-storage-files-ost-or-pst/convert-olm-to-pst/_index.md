---
title: Convert OLM to PST
ArticleTitle: Convert OLM to PST
type: docs
weight: 90
url: /python-net/convert-olm-to-pst/
---


## **Convert OLM to PST**

OLM (Outlook for Mac) is a file format used by Microsoft Outlook for Mac to store email messages, contacts, calendars, tasks, and other data. It is the native file format for Outlook for Mac, so it is not possible to open an Outlook for Mac (OLM) file in Outlook for Windows. To work with OLM files in Windows, Aspose Email provides tools specifically designed to handle OLM files. Its approach is to convert OLM files to PST (Outlook Data File) format, which is widely supported in Windows environments. Once converted to PST format, you can then import the data into Outlook for Windows or any other compatible email client. The following code sample will show you how to convert an OLM to a PST.

**Migration of email data from OLM to PST format**

```py

import aspose.email as ae

# create an instance of OlmStorage class to open source OLM
olm = ae.storage.olm.OlmStorage("my.olm")
# create a new PST file
pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

# recursively reads each folder and its messages
# and adds them to the PST in the same order

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```
**'get_container_class' implementation to categorize different types of Outlook items**

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
**'add_to_pst' function implementation to transfer data from an OLM file to a PST file**

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
