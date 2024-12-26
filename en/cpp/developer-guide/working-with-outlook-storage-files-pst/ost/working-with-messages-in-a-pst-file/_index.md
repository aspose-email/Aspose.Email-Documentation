---
title: Working with Messages in a PST File
ArticleTitle: Working with Messages in a PST File
type: docs
weight: 100
url: /cpp/working-with-messages-in-a-pst-file/
---

## **Adding Messages to PST Files**
Create a New PST File and Add Subfolders showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add messages to subfolders of a PST file that you have created or loaded. This article adds two messages from disk to the Inbox subfolder of a PST. Use the PersonalStorage and FolderInfo classes to add messages to PST files. To add messages to a PST file's Inbox folder:

1. Create an instance of the FolderInfo class and load it with the contents of the Inbox folder.
1. Add messages from disk to the Inbox folder by calling the FolderInfo.AddMessage() method. The FolderInfo class exposes the AddMessages method that enables to add large number of messages to the folder, reducing I/O operations to disc and improving performance. A complete example can be found below, in Adding Bulk Messages.

The code snippets below shows how to add messages to a PST subfolder called Inbox.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMessagesToPSTFiles-AddMessagesToPSTFiles.cpp" >}}
### **Saving Messages Directly from PST to Stream**
To save messages from a PST file directly to stream, without extracting the MsgInfo for messages, use the SaveMessageToStream() method. The following code snippet shows you how to save messages directly from PST to stream.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveMessagesDirectlyFromPSTToStream-SaveMessagesDirectlyFromPSTToStream.cs" >}}
### **Extracting n Number of Messages from a PST File**
The following code snippet shows you how to extract a given number of messages from a PST. Simply provide the index for the first message, and the total number of messages to be extracted.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractNumberOfMessages-ExtractNnumberOfMessages.cpp" >}}
## **Search Messages and Folders in a PST by Criterion**
Personal Storage (PST) files can contain a huge amount of data and searching for data that meets a specific criteria in such large files needs to include multiple check points in the code to filter the information. With the PersonalStorageQueryBuilder class, Aspose.Email makes it possible to search for specific records in a PST based on a specified search criteria. A PST can be searched for messages based on search parameters such as sender, receiver, subject, message importance, presence of attachments, message size, and even message ID. The PersonalStorageQueryBuilder can also be used to search for subfolders.
### **Searching Messages and Folders in PST**
The following code snippet shows you how to use the PersonalStorageQueryBuilder class to search for contents in a PST based on different search criteria. For example, it shows searching a PST based on:

- Message importance.
- Message class.
- Presence of attachments.
- Message size.
- Unread messages.
- Unread messages with attachments, and
- folders with specific subfolder name.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SearchMessagesAndFoldersInPST-SearchMessagesAndFoldersInPST.cpp" >}}
## **Extract Attachments without Extracting Complete Message**
Aspose.Email API can be used to extract attachments from PST messages without extracting the complete message first. The ExtractAttachments method of IEWSClient can be used to do this. The following code snippet shows you how to extract attachments without extracting complete message.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ExtractAttachmentsFromPSTMessages-ExtractAttachmentsFromPSTMessages.cpp" >}}
## **Adding Files to PST**
Microsoft Outlook's key functionality is managing emails, calendars, tasks, contacts and journal entries. In addition, files can also be added to a PST folder and the resulting PST keeps record of the documents added. Aspose.Email provides the facility to add files to a folder in the same way in addition to adding messages, contacts, tasks and journal entries to PST. The following code snippet shows you how to add documents to a PST folder using Aspose.Email.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddFilesToPST-AddFilesToPST.cpp" >}}
