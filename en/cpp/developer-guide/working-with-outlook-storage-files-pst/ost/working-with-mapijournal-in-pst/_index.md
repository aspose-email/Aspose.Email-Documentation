---
title: Working with MapiJournal in PST
type: docs
weight: 70
url: /cpp/working-with-mapijournal-in-pst/
---

## **Adding MapiJournal to PST**
With Aspose.Email you can add MapiJournal to hte Journal subfolder of a PST file that you have created or loaded. Below are the steps to add MapiJournal to a PST:

1. Create a MapiJournal object
1. Set the MapiJournal properties using a constructor and methods.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Journals) at the root of the PST file by accessing the root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiJournal and then add it to the journal folder of a newly created PST file.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}
## **Adding Attachments to MapiJournal**
The following code snippet shows you how to add attachments to MapiJournal.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}
