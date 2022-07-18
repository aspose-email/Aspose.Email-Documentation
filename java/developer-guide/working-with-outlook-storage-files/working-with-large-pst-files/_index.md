---
title: Working with large PST files
type: docs
weight: 130
url: /java/working-with-large-pst-files/
---

Performance may be degraded when processing large PST files.
The following suggestions will help improve the performance of your app when processing large files.

{{% alert color="primary" %}}
Consider methods returning `Iterable` when traversing folders or messages in a pst.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders())
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Do something with message
        }
}
```
{{% alert color="primary" %}}
Prefer [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo) for accessing basic message properties.
{{% /alert %}}

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Subject: " + messageInfo.getSubject());
    System.out.println("To: " + messageInfo.getDisplayTo());
    System.out.println("Importance: " + messageInfo.getImportance());
    System.out.println("Message Class: " + messageInfo.getMessageClass());
}
```
{{% alert color="primary" %}}
Avoid using the [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(byte[]\)) or [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateMapiMessages\(\)) methods for all messages unless you need to have access to all properties.
{{% /alert %}}

{{% alert color="primary" %}}
Consider using [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateMessagesEntryId\(\)) to easily retrieve all message IDs contained in a folder.
{{% /alert %}}

```java
for (String id : folder.enumerateMessagesEntryId())
{
    // Use id to retrieve a property (extractProperty),
    // extract a MapiMessage (extractMessage),
    // extarct message attachments (extractAttachments),
    // save msg to a stream (saveMessageToStream).
}
```
{{% alert color="primary" %}}
Consider using [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractProperty\(byte[],%20long\)) to read a single property that is missing in MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Consider using [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractAttachments\(java.lang.String\)) if only the attachments are required.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use [seach criteria](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst)-based filtering to get the messages you require.
{{% /alert %}}

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

{{% alert color="primary" %}}
Consider using [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#saveMessageToStream\(java.lang.String,%20java.io.OutputStream\)) if it is necessary to save messages from pst.
{{% /alert %}}

Instead of using:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    MapiMessage msg = pst.extractMessage(id);
    msg.save("message.msg");
}
```

Use:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    try (OutputStream fos  = new FileOutputStream("message.msg")) {
        pst.saveMessageToStream(id, fos);
    }
}
```
{{% alert color="primary" %}}
Prefer bulk methods to [add](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) multiple items.
{{% /alert %}}
