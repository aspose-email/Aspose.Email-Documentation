---
title: Working with MapiNote in PST
ArticleTitle: Working with MapiNote in PST
type: docs
weight: 80
url: /cpp/working-with-mapinote-in-pst/
---

## **Adding MapiNote to PST**
With Aspose.Email you can add a MapiNote to the Notes subfolder of a PST file that you have created or loaded. To add a MapiNote to a PST:

1. Create a template MapiNote using Microsoft Outlook and save it as an MSG file.
1. Load the saved MSG note into a MapiMessage object.
1. Create a MapiNote object and load the template MSG note.
1. Set the MapiNote properties.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Notes) at the root of the PST file by accessing the root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiNote and then add it to the notes folder of a newly created PST file.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cpp" >}}
