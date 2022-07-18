---
title: Deleting Messages from POP3 Server
type: docs
weight: 20
url: /java/deleting-messages-from-pop3-server/
---


Aspose.Email is a robust component that allows performing customized operations after certain actions. Aspose.Email fires many events upon which users can perform operations. This feature provides users more control over their application. For example, users can perform their desired actions when:

- All bulk emails have been sent.
- A message is about to send.
- An email is completely sent.
- When a recipient is rejected by the SMTP server.

POP3 mailboxes reside on a POP3 server. The email in these mailboxes can be retrieved to your PC by [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client). The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client) class uses POP3 protocol to copy the mail messages from your POP3 mailbox to your PC. Once the mail has been retrieved you do not need to be connected to the internet while it is being read as you could read the retrieved mail on your PC. If you don't need or want a copy of some mail messages kept on the POP3 server, you then delete it. This section shows how to delete emails using [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client) class.
## **Delete an Email by Index**
The following code snippet deletes all the mail messages of a mailbox one by one, based on its index. Index should never be <=0 in [Pop3Client.deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client#deleteMessage\(int\)).


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create a POP3 client
Pop3Client client = new Pop3Client("mail.aspose.com", 110, "username", "psw");
try {
    // Delete all the message one by one
    int messageCount = client.getMessageCount();
    for (int i = 1; i <= messageCount; i++) {
        client.deleteMessage(i);
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Delete All Emails**
We might also call [Pop3Client.deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client#deleteMessages\(\)) to delete all the messages. The following code snippet shows you how to delete all emails.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Delete all the messages
client.deleteMessages();
~~~
If the connection to the POP3 server is broken immediately after delete operations, you can no longer call [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client).cancelDeletes() to do the things you want.
## **Cancel Deletes**
[Pop3Client.undeleteMessages](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client#undeleteMessages\(\)) can be used to cancel the deletion of email messages. The following code snippet shows you how to cancel deletes.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Cancel deletes
client.undeleteMessages();
~~~
