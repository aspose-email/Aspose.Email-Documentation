---
title: Working with Message Attachments
type: docs
weight: 70
url: /java/working-with-message-attachments/
---

## **Parsing and Saving Attachments**
Outlook message files may contain one or more attachments. Aspose.Email lets developers loop through the attachments in an MSG file and save them to disk. This topic describes the process. It also describes how to embed an attachment.

Aspose.Email's [MapiMessage](https://reference.aspose.com/email//java/com.aspose.email/mapimessage) class is used to load an MSG file from disk and exposes the getAttachments() method which references the [MapiAttachment](https://reference.aspose.com/email//java/com.aspose.email/mapiattachment) object collection associated with the MSG file. The [MapiAttachment](https://reference.aspose.com/email//java/com.aspose.email/mapiattachment) object further exposes methods that perform actions on the attachment.

To save attachments in an MSG file to disk with the original name and extension:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email//java/com.aspose.email/mapimessage) class to load an MSG file using the fromFile() static method.
1. Call the [MapiRecipient](https://reference.aspose.com/email//java/com.aspose.email/mapirecipient) class' getAttachments() method to get a reference to the collection of [MapiAttachment](https://reference.aspose.com/email//java/com.aspose.email/mapiattachment) objects associated with the MSG file.
1. Loop through the [MapiAttachmentCollection](https://reference.aspose.com/email//java/com.aspose.email/mapiattachmentCollection) collection to display contents regarding each [MapiAttachment](https://reference.aspose.com/email//java/com.aspose.email/mapiattachment) object through its public methods.
1. Call the [MapiAttachment](https://reference.aspose.com/email//java/com.aspose.email/mapiattachment) class' save() method to save attachment to the disk.
 

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Embedding Message as Attachments

A Microsoft Outlook message can contain other Microsoft Outlook messages in attachments either as regular messages, described above, or embedded messages. The [MapiAttachmentCollection](https://reference.aspose.com/email//java/com.aspose.email/mapiattachmentCollection) collection provides overloaded members of the add method for creating Outlook messages with both types of attachments. Outlook MSG files embedded in a MSG file contains a PR_ATTACH_METHOD with the value 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}


### **Reading Embedded Message from Attachment**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}
## **Attachments MSG Insertion and Replacement**
Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment.
### **Insert MSG Attachment at Specific Location**
Aspose.Email API provides the capability to insert a MSG attachment to a parent MSG using the [MapiAttachmentCollection's](https://reference.aspose.com/email//java/com.aspose.email/mapiattachmentCollection) insert method.
MapiAttachmentCollection insert(int, String, MapiMessage)

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}


### **Replace Embedded MSG Attachment Contents**
This can be used to replace embedded attachment contents with the new ones using the Replace method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}


## **Save Attachments from Digitally Signed Message**
Aspose.Email API provides the capability to get or set a value indicating whether clear-signed message will be decoded. 

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}
