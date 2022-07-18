---
title: Working with MapiJournal in PST
type: docs
weight: 70
url: /java/working-with-mapijournal-in-pst/
---

## **Adding MapiJournal to PST**
[Create New PST, Add Sub-folders and Messages](/email/java/create-new-pst-add-sub-folders-and-messages/) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add MapiJournal to the Journal subfolder of a PST file that you have created or loaded. Below are the steps to add MapiJournal to a PST:

1. Create a [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/MapiJournal) object.
1. Set the [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/MapiJournal) properties using a constructor and methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#create\(java.io.OutputStream,%20int\)) method.
1. Create a pre-defined folder (Journals) at the root of the PST file by accessing the root folder and then calling the [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMapiMessageItem\(com.aspose.email.IMapiMessageItem\)) method.

The code snippet below shows how to create a [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/MapiJournal) and then add it to the Journal folder of a newly created PST file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}
## **Adding Attachments to MapiJournal**
It is also possible to add attachments to MAPI journal items. The code below shows how.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}
