---
title: Managing Outlook MAPI Notes in PST Files
ArticleTitle: Managing Outlook MAPI Notes in PST Files
type: docs
weight: 80
url: /python-net/managing-outlook-mapinotes-in-pst/
---


## **Add Outlook MAPI Notes to PST Files**

[Create a New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) shows how to create a new PST file and add a subfolder to it. With Aspose.Email you can also create MAPI notes and store them in a PST file. The code sample below creates three MAPI notes of different characteristics, adds them to a PST file within a designated folder, and then safely closes the file. 

1. [MapiNote](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinote/) objects are created setting the subject, body, color, and height and width, if necessary.
2. A new PST file is created using [PersonalStorage.create](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) specifying the UNICODE format.
3. Within the PST file, a predefined folder named "Tasks" is created to store the notes. 
4. Each of the MAPI notes (note1, note2, and note3) is added to the notesFolder using the [add_mapi_message_item](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method. This process integrates the notes into the PST structure for storage.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}
