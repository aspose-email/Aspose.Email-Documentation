---
title: Managing Tasks, Journals, and Notes in PST Files
ArticleTitle: Managing Tasks, Journals, and Notes in PST Files
type: docs
weight: 60
url: /net/managing-tasks-journals-and-notes-in-pst-files/
---


## **Add MAPI Task to PST**

The [Creating and Managing PST Files](https://docs.aspose.com/email/net/create-and-manage-pst-files/) article shows how to create a PST file and add a subfolder to it. With Aspose.Email you can add [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) to the Tasks subfolder of a PST file that you have created or loaded. Below are the steps to add MapiTask to a PST:

1. Create a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) object.
2. Set the [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) properties using constructor and different methods.
3. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Create a pre-defined folder (Tasks) at the root of the PST file by accessing the Root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) and then add it to the tasks folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}

## **Add MAPI Journal to PST**

Aspose.Email also allows you to add [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) to the Journal subfolder of a PST file that you have created or loaded. Below are the steps to add [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) to a PST:

1. Create a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) object
2. Set the [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) properties using a constructor and methods.
3. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Create a pre-defined folder (Journals) at the root of the PST file by accessing the root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) and then add it to the journal folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Add Attachments to MAPI Journal**

The following code snippet shows you how to add attachments to [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}

## **Add MAPI Note to PST**

With Aspose.Email you can add a [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) to the Notes subfolder of the created or loaded PST file. To add a [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) to a PST:

1. Create a template [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) using Microsoft Outlook and save it as an MSG file.
2. Load the saved MSG note into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
3. Create a [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) object and load the template MSG note.
4. Set the [MapiNote properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
6. Create a pre-defined folder (Notes) at the root of the PST file by accessing the root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) and then add it to the notes folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}
