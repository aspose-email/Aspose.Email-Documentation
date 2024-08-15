---
title: Working with Outlook Notes
type: docs
weight: 100
url: /python-net/working-with-outlook-notes/
---


## **Creating, Saving and Reading Notes**
Aspose.Email provides the facility to create Outlook notes and save them to disc in MSG format. The MapiNote class provides properties and methods for setting task information. This articles shows how to create, save and read a MapiNote from disc.
### **Creating and Saving an Outlook Note**
The following steps can be used to create and save a note to disc:

1. Instantiate an object of the MapiNote class.
1. Set various properties.
1. Save the note to disc as an MSG file.

The following code snippet shows you how to creating and saving an outlook Note.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveOutlookNote-CreateAndSaveOutlookNote.py" >}}
### **Reading a MapiNote**
The MapiNote class object is used to cast the MapiMessage object that loads a note from disc in MSG format. The following code snippet shows you how to read a MapiNote.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingMapiNote-ReadingMapiNote.py" >}}
