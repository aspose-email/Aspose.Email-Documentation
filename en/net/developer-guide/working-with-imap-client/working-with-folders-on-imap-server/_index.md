---
title: Working with Folders on IMAP Server
type: docs
weight: 60
url: /net/working-with-folders-on-imap-server/
---


## **Getting Folders Information**

Getting information about folders from an IMAP server is very easy with Aspose.Email. Call the [ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) method of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class. It returns an object of the [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/) type. Iterate through this collection and get information about individual folders in a loop. The method is overloaded. You can pass a folder name as a parameter to get a list of subfolders. The following code snippet shows you how to get folder information from an IMAP server using Aspose.Email using the method described in the information.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Deleting and Renaming Folders**

A folder on an IMAP server can be deleted or renamed in a single line with Aspose.Email:

- The [DeleteFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) method accepts the folder name as a parameter.
- For the [RenameFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/) method, you need to pass the current folder name and new folder name.
  The following code snippet shows you how to remove a folder from an IMAP server, and how to rename a folder. Each operation is performed with one line of code.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Adding a New Message in a Folder**

You can add a new message to the folder using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) classes. First create a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object by providing the subject, to and from values. Then subscribe to a folder and add the message to it. The following code snippet shows you how to add a new Message in a folder.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Add Multiple Messages with MultiConnection Support**

You can add multiple messages by using the [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) method provided by the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) classes. The [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) method accepts a list of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) and adds it to the current folder if the folder is not provided as a parameter. ImapClient also supports MultiConnection mode for heavy loaded operations. The following code snippet shows you how to add multiple messages by using the MultiConnection mode.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 

## **Move Messages to Another Mailbox Folder**

Aspose.Email for .NET allows moving message from one mailbox folder to another using the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API. The [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) method uses the message unique id and destination folder name for moving a message to the destination folder. The following code snippet shows you how to move messages to another mailbox folder.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Copy Messages to Another Mailbox Folder**

Aspose.Email API provides the capability to copy message from one mailbox folder to another. It allows copying a single as well as multiple messages using the [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) and [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) methods. The [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) method provides the capability to copy multiple messages from source folder of a mailbox to the destination mailbox folder. The following code snippet shows you how to copy messages to another mailbox folder.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Working with Special-Use Mailbox Folders**

Some IMAP message stores include special-use mailboxes, such as those used to hold draft messages or sent messages. Many mail clients allow users to specify where the draft or sent messages should be put, but configuring them requires that the user knows which mailboxes the server has set aside for these purposes. Aspose.Email can identify these special-use mailboxes by using the [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) class to make it easier to work with them. The following code sample demonstrates how to access these special-use mailboxes by using the [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) class.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}
