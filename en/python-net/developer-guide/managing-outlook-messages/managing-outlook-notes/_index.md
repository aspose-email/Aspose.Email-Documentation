---
title: Managing Outlook Notes
ArticleTitle: Managing Outlook Notes
type: docs
weight: 100
url: /python-net/managing-outlook-notes/
---


## **Create and Save Outlook Notes**

Aspose.Email offers the capability to create Outlook notes and save them to disk in MSG format. The [MapiNote](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinote/) class includes properties and methods for configuring task details. The following code sample demonstrates how to create and save a MapiNote to disk.

1. Initialize a MapiNote object by creating an instance of the [MapiNote](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinote/) class.
1. Set Note properties: subject, body, color, dimensions  .
1. Save the Note to disk in MSG format specifying the file path.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveOutlookNote-CreateAndSaveOutlookNote.py" >}}

## **Read MapiNote Files**

The [MapiNote](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapinote/) class is used to represent a note, loaded from a disk in MSG format, within a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) object . Below is a code snippet demonstrating how to read a MapiNote:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingMapiNote-ReadingMapiNote.py" >}}
