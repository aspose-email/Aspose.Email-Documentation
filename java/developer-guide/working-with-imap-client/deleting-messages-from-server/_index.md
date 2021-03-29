---
title: Deleting Messages from Server
type: docs
weight: 50
url: /java/deleting-messages-from-server/
---


## **Deleting Messages**
The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class can delete messages from an IMAP server. The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class [deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#deleteMessage\(int\)) function is used to delete messages. It takes the message sequence number or unique ID as a parameter. The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) provides [deleteMessage](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#deleteMessage\(int\)) and [deleteMessages](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#deleteMessagesBySequences\(com.aspose.email.IConnection,%20java.lang.Iterable\)) methods for deleting messages one by one or multiple. The following code snippet shows you how to delete an email message with the message ID 1 from an IMAP server.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    try {
        System.out.println(client.getUidPlusSupported());
        // Append some test messages
        client.selectFolder(ImapFolderInfo.IN_BOX);
        MailMessage message = new MailMessage("from@Aspose.com", "to@Aspose.com", "EMAILNET-35227 - " + UUID.randomUUID(),
                "EMAILNET-35227 Add ability in ImapClient to delete message");
        String emailId = client.appendMessage(message);

        // Now verify that all the messages have been appended to the mailbox
        ImapMessageInfoCollection messageInfoCol = null;
        messageInfoCol = client.listMessages();
        System.out.println(messageInfoCol.size());

        // Select the inbox folder and Delete message
        client.selectFolder(ImapFolderInfo.IN_BOX);
        client.deleteMessage(emailId);
        client.commitDeletes();
    } finally {

    }
} finally {
    if (client != null)
        client.dispose();
}
~~~
## **Deleting Multiple Messages**
Multiple emails can be deleted from mailbox using the [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) of Aspose.Email API. The [deleteMessages](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#deleteMessagesBySequences\(com.aspose.email.IConnection,%20java.lang.Iterable\)) method provides a number of options to delete multiple messages from the server using unique ids, sequence numbers or [ImapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection) elements. The following code snippet shows you how to delete multiple messages.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    try {
        System.out.println(client.getUidPlusSupported());
        // Append some test messages
        client.selectFolder(ImapFolderInfo.IN_BOX);
        List<String> uidList = new ArrayList<String>();
        final int messageNumber = 5;
        for (int i = 0; i < messageNumber; i++) {
            MailMessage message = new MailMessage("from@Aspose.com", "to@Aspose.com", "EMAILNET-35226 - " + UUID.randomUUID(),
                    "EMAILNET-35226 Add ability in ImapClient to delete messages and change flags for set of messages");
            String uid = client.appendMessage(message);
            uidList.add(uid);
        }

        // Now verify that all the messages have been appended to the mailbox
        ImapMessageInfoCollection messageInfoCol = null;
        messageInfoCol = client.listMessages();
        System.out.println(messageInfoCol.size());

        // Bulk Delete Messages and Verify that the messages are deleted
        client.deleteMessagesByUids(uidList, true);
        client.commitDeletes();
        messageInfoCol = null;
        messageInfoCol = client.listMessages();
        System.out.println(messageInfoCol.size());
    } finally {

    }
} finally {
    if (client != null)
        client.dispose();
}
~~~
