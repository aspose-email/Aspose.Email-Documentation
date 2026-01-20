---
title: Working with large PST files
ArticleTitle: Working with large PST files
type: docs
weight: 130
url: /java/working-with-large-pst-files/
---

Processing large Personal Storage Table (PST) files can reduce performance and increase memory usage. Aspose.Email for Java provides several techniques and APIs that allow developers to access, process, and manage mailbox data efficiently without overloading system resources.

## **Use Iterable Methods for Traversing Folders and Messages**

When iterating through folders and messages, prefer methods that return `Iterable`. This reduces memory overhead and improves performance.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Process message
        }
    }
}
```

## **Use MessageInfo for Basic Message Properties**

If you need only basic message details, use [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) instead of loading the full message. This is faster and consumes less memory. 

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Subject: " + messageInfo.getSubject());
    System.out.println("To: " + messageInfo.getDisplayTo());
    System.out.println("Importance: " + messageInfo.getImportance());
    System.out.println("Message Class: " + messageInfo.getMessageClass());
}
```

## **Avoid Extracting Full Messages Unless Necessary**


Do not use [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) or [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) methods for all messages unless you need all properties.

Instead, consider:

**a) Retrieving Message IDs**

Use `enumerateMessagesEntryId` to get all message IDs in a folder. You can then selectively extract properties, messages, or attachments.

```java
for (String id : folder.enumerateMessagesEntryId()) {
    // Retrieve a property using ID (extractProperty),
    // Extract a MapiMessage (extractMessage),
    // Extract message attachments (extractAttachments),
    // Save message to a stream (saveMessageToStream).
}
```

**b) Extracting a Single Property**

Use `ExtractProperty` if you need only a specific property missing in [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
        pst.extractProperty(
            org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
            KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()
        ).getString();
}
```

**c) Extracting Attachments Only**

If only attachments are needed, use `ExtractAttachments`.

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

## **Use Search Criteria to Filter Messages**

Filtering messages using [seach criteria](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) reduces the number of messages loaded and improves performance.


```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {

    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);

    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        MessageInfoCollection unread = folder.getContents(builder.getQuery());
    }
}
```

## **Save Messages to Stream**


Instead of extracting and saving messages one by one, use [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) for better performance. 


```java
for (String id : folder.enumerateMessagesEntryId()) {
    try (OutputStream fos  = new FileOutputStream("message.msg")) {
        pst.saveMessageToStream(id, fos);
    }
}
```

## **Use Bulk Methods When Possible**

Whenever you need to [add](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) multiple items, prefer bulk methods over individual operations. This reduces overhead and improves performance.


