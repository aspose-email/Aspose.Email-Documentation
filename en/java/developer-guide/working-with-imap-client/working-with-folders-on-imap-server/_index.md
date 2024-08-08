---
title: Working with Folders on IMAP Server
type: docs
weight: 60
url: /java/working-with-folders-on-imap-server/
---


## **Getting Folders Information**

Getting information about folders from an IMAP server is very easy with Aspose.Email. Call the [listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) method of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class. It returns an object of the [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/) type. Iterate through this collection and get information about individual folders in a loop. The method is overloaded. You can pass a folder name as a parameter to get a list of subfolders. The following code snippet shows you how to get folder information from an IMAP server using the described Aspose.Email method.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get all folders in the currently subscribed folder
ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Iterate through the collection to get folder info one by one
for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoColl) {
    // Folder name and get New messages in the folder
    System.out.println("Folder name is " + folderInfo.getName());
    ImapFolderInfo folderExtInfo = client.getFolderInfo(folderInfo.getName());
    System.out.println("New message count: " + folderExtInfo.getNewMessageCount());
    System.out.println("Is it readonly? " + folderExtInfo.getReadOnly());
    System.out.println("Total number of messages " + folderExtInfo.getTotalMessageCount());
}
~~~

## **Deleting and Renaming Folders**

A folder on an IMAP server can be deleted or renamed in a single line with Aspose.Email:

- The [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) method accepts the folder name as a parameter.
- For the [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-) method, you need to pass the current folder name and new folder name.
  The following code snippet shows you how to remove a folder from an IMAP server, and how to rename a folder. Each operation is performed with one line of code.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Delete a folder and Rename a folder
client.deleteFolder("foldername");
client.renameFolder("foldername", "newfoldername");
~~~

## **Adding a New Message in a Folder**

You can add a new message to the folder using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) classes. First, create a [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) object by providing the subject, to and from values. Then subscribe to a folder and add the message to it. The following code snippet shows you how to add a new message to a folder.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Subscribe to the Inbox folder and Append the newly created message
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~

## **Add Multiple Messages with MultiConnection Support**

You can add multiple messages by using the [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) method provided by the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class. The [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) method accepts a list of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) and adds it to the current folder if the folder is not provided as a parameter. ImapClient also supports MultiConnection mode for heavy loaded operations. The following code snippet shows you how to add multiple messages by using the MultiConnection mode.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Test Message - " + UUID.randomUUID().toString(), "IMAP Group Append with MultiConnection");
    messages.add(message);
}

imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
imapClient.appendMessages(messages);
~~~

{{% alert color="primary" %}} 

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 

## **Move Messages to Another Mailbox Folder**

Aspose.Email for Java allows to move a message from one mailbox folder to another using the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API. The [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) method uses the message unique id and destination folder name for moving a message to the destination folder. The following code snippet shows you how to move messages to another mailbox folder.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows how to move a message from one folder of a mailbox to another one using the ImapClient API of Aspose.Email for Java
// Available from Aspose.Email for Java onwards
// -------------- Available API Overload Members --------------
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName)
// void ImapClient.moveMessage(int sequenceNumber, String folderName)
// void ImapClient.moveMessage(String uniqueId, String folderName)

final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    String folderName = "EMAILNET-35151";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35151 - " + UUID.randomUUID(),
                "EMAILNET-35151 ImapClient: Provide option to Move Message");
        client.selectFolder(ImapFolderInfo.IN_BOX);
        // Append the new message to Inbox folder
        String uniqueId = client.appendMessage(ImapFolderInfo.IN_BOX, message);
        ImapMessageInfoCollection messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Now move the message to the folder EMAILNET-35151
        client.moveMessage(uniqueId, folderName);
        client.commitDeletes();
        // Verify that the message was moved to the new folder
        client.selectFolder(folderName);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Verify that the message was moved from the Inbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Copy Messages to Another Mailbox Folder**

Aspose.Email API provides the capability to copy a message from one mailbox folder to another. It allows copying a single as well as multiple messages using the [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) and [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) methods. The [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) method provides the capability to copy multiple messages from source folder of a mailbox to the destination mailbox folder. The following code snippet shows you how to copy messages to another mailbox folder.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    // Create the destination folder
    String folderName = "EMAILNET-35242";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        // Append a couple of messages to the server
        MailMessage message1 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId1 = client.appendMessage(message1);

        MailMessage message2 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId2 = client.appendMessage(message2);

        // Verify that the messages have been added to the mailbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());

        // Copy multiple messages using the CopyMessages command and Verify that messages are copied to the destination folder
        client.copyMessagesByUids(Arrays.asList(uniqueId1, uniqueId2), folderName);

        client.selectFolder(folderName);
        msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Working with Special-Use Mailbox Folders**

Some IMAP message stores include special-use mailboxes, such as those used to hold draft messages or sent messages. Many mail clients allow users to specify where the draft or sent messages should be put, but configuring them requires that the user knows which mailboxes the server has set aside for these purposes. Aspose.Email can identify these special-use mailboxes by using the [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) class to make it easier to work with them. The following code sample demonstrates how to access these special-use mailboxes by using the [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) class.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();
System.out.println(mailboxInfo.getInbox());
System.out.println(mailboxInfo.getDraftMessages());
System.out.println(mailboxInfo.getJunkMessages());
System.out.println(mailboxInfo.getSentMessages());
System.out.println(mailboxInfo.getTrash());
~~~
