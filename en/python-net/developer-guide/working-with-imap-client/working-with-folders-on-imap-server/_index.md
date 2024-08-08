---
title: Working with Folders on IMAP Server
type: docs
weight: 50
url: /python-net/working-with-folders-on-imap-server/
---


## **Getting Folders Information**
Getting information about folders from an IMAP server is very easy with Aspose.Email. Call the Aspose.Email.Imap namespace's ListFolders() method. It returns an object of the [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection) type. Iterate through this collection and get information about individual folders in a loop. The method is overloaded. You can pass a folder name as a parameter to get a list of subfolders. The following code snippet shows you how to get folder information from an IMAP server using Aspose.Email using the method described in the information.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Deleting and Renaming Folders**

The following methods of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class related to managing folders on an email server using IMAP can be easily implemented into your project with Aspose.Email:

- delete_folder method - permanently removes the folder and all of the messages contained within it.
- rename_folder method - changes the name of the folder without altering the contents within it.

The code snippet below shows how to delete or rename folders on the IMAP server programmatically:

```py
# Delete a folder and Rename a folder
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Adding a New Message in a Folder**
You can add a new message to the folder using the MailMessage class and ImapClient classes. To First create a MailMessage object by providing the subject, to and from values. Then subscribe to a folder and add the message to it. The following code snippet shows you how to add a new Message in a folder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Establishing MultiConnection when Performing Batch Operations**

Aspose.Email makes it possible to configure the client to establish multiple simultaneous connections to the IMAP server. It does not necessarily increase the performance, but it's a reliable solution for concurrent operations. This is particularly useful if the client needs to perform multiple tasks at the same time, such as fetching different email folders, synchronizing large amounts of data, or processing multiple messages simultaneously. 

The code snippet below shows how to establish multiple connections to the IMAP server while uploading a collection of email messages using the 'append_messages' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```

## **Move Messages to Another Mailbox Folder**
Aspose.Email for .NET allows to move message from one mailbox folder to another using the ImapClient API. The MoveMessage method uses the message's unique id and destination folder name for moving a message to the destination folder. The following code snippet shows you how to move messages to another mailbox folder.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}
## **Copy Messages to Another Mailbox Folder**
Aspose.Email API provides the capability to copy message from one mailbox folder to another. It allows to copy a single as well as multiple messages using the CopyMessage and CopyMessages methods. The CopyMessages method provides the capability to copy multiple messages from source folder of a mailbox to the destination mailbox folder. The following code snippet shows you how to copy messages to another mailbox folder. 



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Working with Special-Use Mailbox Folders**

Special-use mailboxes are pre-designated folders within an email system used for specific types of messages, such as Sent, Drafts, Junk, Trash, and Archive. The Aspose.Email library allows for the access to these mailboxes by assigning attributes associated with their roles and purposes to the client. The clients then can automatically discover and present these folders accordingly without user intervention.

The following code snippet shows how to query information about the important special-use mailboxes (inbox, draft, junk, sent, and trash) using the properties of the [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class) class, and print out this information:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```