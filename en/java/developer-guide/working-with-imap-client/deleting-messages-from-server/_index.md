---
title: Deleting Messages from Server
type: docs
weight: 50
url: /java/deleting-messages-from-server/
---


## **Deleting Messages**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class can delete messages from an IMAP server. The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) function is used to delete messages. It takes the message sequence number or unique ID as a parameter. The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) and [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) methods for deleting messages one by one or multiple. The following code snippet shows you how to delete an email message with the message ID 1 from an IMAP server.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Append test message
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Message to delete");
    eml.setBody("Hey! This Message will be deleted!");
    String emlId = client.appendMessage(eml);

    // Delete appended message
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Deleting Multiple Messages**

Multiple emails can be deleted from mailbox using the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) of Aspose.Email API. The [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) method provides a number of options to delete multiple messages from the server using unique ids, sequence numbers or [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) elements. The following code snippet shows you how to delete multiple messages.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Append test messages
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Message to delete " + i);
        eml.setBody("Hey! This Message will be deleted!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Bulk Delete appended Messages
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~
