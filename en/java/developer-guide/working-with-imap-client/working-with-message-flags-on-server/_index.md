---
title: Working with Message Flags on Server
ArticleTitle: Working with Message Flags on Server
type: docs
weight: 30
url: /java/working-with-message-flags-on-server/
---


## **Changing the Message Flags**

You can change message flags by using the [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) method. This method takes two parameters.

1. The message sequence number or unique ID.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

The following flags can be set:

- [Answered](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Deleted](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Draft](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Empty](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Flagged](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [isRead](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Recent](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
  
### **Setting Message Flags**

The following code snippet shows you how to change message flags on an IMAP server with Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Mark the message as read
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Removing Message Flags**

Message flags can also be removed with the [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) method. Usage is similar to that of the [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) method. It takes a sequence number or unique message ID and [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). The following code snippet shows you how to remove message flags.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Remove the message flag
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Setting Custom Flags**

You can also set custom flags to a message using the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) of the API. The ImapClient [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) provides the ability to set custom flags on messages.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Append the message to mailbox
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Add custom flags to the added messge
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Retreive the messages for checking the presence of custom flag
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Keyword found");
}
~~~
