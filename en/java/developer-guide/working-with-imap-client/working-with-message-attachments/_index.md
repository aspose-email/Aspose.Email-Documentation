---
title: Working with Message Attachments using IMAP
type: docs
weight: 30
url: /java/working-with-message-attachments-using-imap/
---


## **List Message Attachments using the IMAP Client**

To get information about attachments such as name, size without fetching the attachment data, use the following API features:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Represents an attachment information. 
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Represents a collection of ImapAttachmentInfo. 
- [listAttachments(int sequenceNumber)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Gets an information for each attachment in a message.

The following code sample shows how to use the IMAP client to retrieve information about email messages and their attachments from a server and then display the attachment details for each message. It allows you to access and process attachments from email messages using the IMAP protocol.

```java
ImapMessageInfoCollection messageInfoCollection = imapClient.listMessages();

for (ImapMessageInfo message : messageInfoCollection) {
    ImapAttachmentInfoCollection attachmentInfoCollection =
            imapClient.listAttachments(message.getSequenceNumber());

    for (ImapAttachmentInfo attachmentInfo : attachmentInfoCollection) {
        System.out.println(
                "Attachment: " + attachmentInfo.getName() + " (size: " + attachmentInfo.getSize() + ")");
    }
}
```


