---
title: Create, Save, and Read Outlook Notes in C++
ArticleTitle: Create, Save, and Read Outlook Notes in C++
type: docs
weight: 100
url: /cpp/create-read-outlook-mapi-notes/
description: Create, save, and load Outlook notes in MSG format using the MapiNote class in C++ with Aspose.Email.
---

**Aspose.Email for C++** allows you to create and manage Outlook Notes programmatically. The [MapiNote](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_note/) class provides all essential properties - such as subject, body text, color, and size - to build and customize a note.

This article demonstrates how to create, save, and read Outlook notes stored in MSG format.


## **Create and Save an Outlook Note**

To create and save an Outlook note to disk, follow the steps below:

1. Instantiate a [MapiNote](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_note/) object.
2. Set note properties such as subject, body, color, height, and width.
3. Save the note to disk in MSG format.

The following code sample demonstrates how to create a colored sticky note with custom dimensions and save it as an Outlook message file.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatAndSaveAnOutlookNote-CreatAndSaveAnOutlookNote.cpp" >}}

## **Read an Outlook Note**

A note saved as an MSG file can be loaded as a [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) and then cast to a [MapiNote](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_note/) object.


The following code sample demonstrates how to load a sticky note from an Outlook MSG file and convert it to a MapiNote object.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadMapiNote-ReadMapiNote.cpp" >}}
