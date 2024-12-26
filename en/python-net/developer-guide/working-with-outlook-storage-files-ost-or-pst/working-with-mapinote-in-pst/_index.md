---
title: Working with MapiNote in PST
ArticleTitle: Working with MapiNote in PST
type: docs
weight: 80
url: /python-net/working-with-mapinote-in-pst/
---


## **Adding MapiNote to PST**
Create a New PST File and Add Subfolders showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add a MapiNote to the Notes subfolder of a PST file that you have created or loaded. To add a MapiNote to a PST:

1. Create a template MapiNote using Microsoft Outlook and save it as an MSG file.
1. Load the saved MSG note into a MapiMessage object.
1. Create a MapiNote object and load the template MSG note.
1. Set the MapiNote properties.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Notes) at the root of the PST file by accessing the root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiNote and then add it to the notes folder of a newly created PST file.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}
