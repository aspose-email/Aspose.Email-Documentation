---
title: Working with Message Attachments
type: docs
weight: 70
url: /java/working-with-message-attachments/
---

## **Parsing and Saving Attachments**

Outlook message files may contain one or more attachments. Aspose.Email lets developers loop through the attachments in an MSG file and save them to disk. This topic describes the process. It also describes how to embed an attachment.

Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class is used to load an MSG file from disk and exposes the [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) method which references the [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) object collection associated with the MSG file. The [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) object further exposes methods that perform actions on the attachment.

To save attachments in an MSG file to disk with the original name and extension:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class to load an MSG file using the [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) static method.
2. Call the [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) class [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) method to get a reference to the collection of [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) objects associated with the MSG file.
3. Loop through the [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) to display contents regarding each [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) object through its public methods.
4. Call the [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) class [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) method to save attachment to the disk.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Embedding Messages as Attachments

A Microsoft Outlook message can contain other Microsoft Outlook messages in attachments either as regular messages, described above, or embedded messages. The [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/)  provides overloaded members of the add method for creating Outlook messages with both types of attachments. Outlook MSG files embedded in a MSG file contains a PR_ATTACH_METHOD with the value 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Reading an Embedded Message from an Attachment**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Attachments MSG Insertion and Replacement**

Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment.

### **Insert MSG Attachment at Specific Location**

Aspose.Email API provides the capability to insert an MSG attachment to a parent MSG using the [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-) method.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Replace Embedded MSG Attachment Contents**

This can be used to replace embedded attachment contents with the new ones using the [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-) method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Save Attachments from Digitally Signed Message**

Aspose.Email API provides the capability to get or set a value indicating whether clear-signed message will be decoded. 

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Rename an Attachment in a MapiMessage**

Aspose.Email makes it possible to edit the [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) property value in [MapiMessage attachments](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

The following code sample demonstrates how to update the display names of the first and second attachments within the loaded Mapi message:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("New display name 1");
msg.getAttachments().get_Item(1).setDisplayName("New display name 2");
```
## **Check if an Attachment is Inline or Regular**

The difference between inline and regular attachments is how they are presented within an email. Inline attachments are embedded within the body of the email and can be viewed without having to open a separate file or download anything. Regular attachments, on the other hand, are separate files that are attached to the email but are not displayed directly within the body of the message and need to be downloaded and opened externally. The [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) property of the [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) class gets a value indicating whether the attachment is inline or regular.

The following code sample loads an email message from a file and then retrieves information about the attachments, specifically printing the display name of each attachment and whether it is inline within the message or not:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```

