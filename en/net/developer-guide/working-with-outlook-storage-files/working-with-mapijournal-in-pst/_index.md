---
title: Working with MapiJournal in PST
type: docs
weight: 70
url: /net/working-with-mapijournal-in-pst/
---


## **Adding MapiJournal to PST**

The [Create a New PST File and Add Subfolders](https://docs.aspose.com/email/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) article shows how to create a PST file and add a subfolder to it. With Aspose.Email you can add [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) to the Journal subfolder of a PST file that you have created or loaded. Below are the steps to add [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) to a PST:

1. Create a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) object
2. Set the [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) properties using a constructor and methods.
3. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Create a pre-defined folder (Journals) at the root of the PST file by accessing the root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) and then add it to the journal folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Adding Attachments to MapiJournal**

The following code snippet shows you how to add attachments to [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}
