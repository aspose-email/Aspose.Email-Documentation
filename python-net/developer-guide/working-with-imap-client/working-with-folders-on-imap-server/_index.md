---
title: Working with Folders on IMAP Server
type: docs
weight: 50
url: /python-net/working-with-folders-on-imap-server/
---


## **Getting Folders Information**
Getting information about folders from an IMAP server is very easy with Aspose.Email. Call the Aspose.Email.Imap namespace's ListFolders() method. It returns an object of the [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection) type. Iterate through this collection and get information about individual folders in a loop. The method is overloaded. You can pass a folder name as a parameter to get a list of subfolders. The following code snippet shows you how to get folder information from an IMAP server using Aspose.Email using the method described in the information.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}
## **Adding a New Message in a Folder**
You can add a new message to the folder using the MailMessage class and ImapClient classes. To First create a MailMessage object by providing the subject, to and from values. Then subscribe to a folder and add the message to it. The following code snippet shows you how to add a new Message in a folder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}
## **Move Messages to Another Mailbox Folder**
Aspose.Email for .NET allows to move message from one mailbox folder to another using the ImapClient API. The MoveMessage method uses the message's unique id and destination folder name for moving a message to the destination folder. The following code snippet shows you how to move messages to another mailbox folder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}
## **Copy Messages to Another Mailbox Folder**
Aspose.Email API provides the capability to copy message from one mailbox folder to another. It allows to copy a single as well as multiple messages using the CopyMessage and CopyMessages methods. The CopyMessages method provides the capability to copy multiple messages from source folder of a mailbox to the destination mailbox folder. The following code snippet shows you how to copy messages to another mailbox folder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}
