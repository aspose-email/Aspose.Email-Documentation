---
title: Working with Attachments and Embedded Objects
type: docs
weight: 20
url: /java/working-with-attachments-and-embedded-objects/
---

## **Managing Email Attachments**
Email messages can contain attachments, files that are included either to improve the look and layout of the message, or files that the sender wants to share with the recipient. Sometimes, developers need to access and manipulate a message's attachments. Aspose.Email Java provides a handful of collections and methods for this purpose. Furthermore, it allows developers to add or remove attachments at run time. To demonstrate these features, this article loads an email message from the disk and accesses its attachment collection.
{{% alert %}}
**Try it out!**

Add or remove email attachments with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}
### **Adding Attachment**
The code below shows how to add several attachments to an email message, after first creating the message.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-AddAttachmentToANewEmailMessage-.java" >}}
### **Removing an Attachment**
The following sequence of steps adds and then removes attachments from an existing message:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class.
1. Load an email message using the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [load()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#load\(java.io.InputStream\)) method, specifying the correct [MessageFormat](https://apireference.aspose.com/java/email/com.aspose.email/messageformat).
1. Create an instance of the [AttachmentCollection](https://apireference.aspose.com/java/email/com.aspose.email/attachmentcollection) class and fill it with attachments from the instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class using the [getAttachments()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#getAttachments\(\)) method.
1. Remove any attachment at any indexed position by calling the [AttachmentCollection](https://apireference.aspose.com/java/email/com.aspose.email/attachmentcollection) collection's removeAt() method.
1. Add an attachment by calling the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [addAttachment()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAttachment\(com.aspose.email.Attachment\)) method, passing an instance of the [Attachment](https://apireference.aspose.com/java/email/com.aspose.email/attachment) class as a parameter.
1. Save the message to disk with the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [save()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) method, specifying the correct [MailMessageSaveType](https://apireference.aspose.com/java/email/com.aspose.email/mailmessagesavetype).



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-AddOrRemoveAttachmentFromAnExistingMessage-.java" >}}
### **Displaying Attachment File Name**
To display the attachment file name, follow these steps:

1. Loop through the attachments in the email message and
   1. Save each attachment.
   1. Display each attachment's name on the screen.

The following code snippet shows you how to display an attachment file name on the screen.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayAttachmentFileName-DisplayAttachmentFileName.java" >}}
### **Extracting Email Attachments**
To save attachments from existing messages:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class.
1. Load the existing email message using the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [load()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#load\(java.io.InputStream\)) method, specifying the correct [MessageFormat](https://apireference.aspose.com/java/email/com.aspose.email/messageformat).
1. Create an instance of the [AttachmentCollection](https://apireference.aspose.com/java/email/com.aspose.email/attachmentcollection) class and fill it with attachments from the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) instance using the [getAttachments()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#getAttachments\(\)) method.
1. Iterate over the [AttachmentCollection](https://apireference.aspose.com/java/email/com.aspose.email/attachmentcollection) collection.
1. Create an instance of the [Attachment](https://apireference.aspose.com/java/email/com.aspose.email/attachment) class and fill it with the indexed value from the [AttachmentCollection](https://apireference.aspose.com/java/email/com.aspose.email/attachmentcollection) using the get_Item() method.
1. Save the attachment to disk using the [Attachment](https://apireference.aspose.com/java/email/com.aspose.email/attachment) class' [save()](https://apireference.aspose.com/java/email/com.aspose.email/AttachmentBase#save\(java.io.OutputStream\)) method.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExtractAttachments-.java" >}}
#### **Retrieving Content-Description from Attachment**
Content-Description information about an attachment can be retrieved from attachment headers as shown in the following code sample.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RetrieveContentDescriptionInformationFromAttachmentHeaders-.java" >}}
#### **Determining if Attachment is Embedded Message**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetermineIfAttachmentIsEmbeddedMessage-.java" >}}
## **Working with Embedded Objects**
### **Embedding Objects into an Email**
With Aspose.Email Java developers can easily embed any image into an email message as well as attach it by using the [LinkedResource](https://apireference.aspose.com/java/email/com.aspose.email/linkedresource) class.

The example below shows how to use the [LinkedResource](https://apireference.aspose.com/java/email/com.aspose.email/linkedresource) class to embed an image:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class.
1. Set the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) object's properties, for example, subject, from, to and CC.
1. Set the HtmlBody with an extra <img> tag.
1. Set the image source using the pattern <img src=[cid:abc](http://cidabc)>.
1. Create an instance of the [LinkedResource](https://apireference.aspose.com/java/email/com.aspose.email/linkedresource) class by supplying the path to the image in the constructor.
1. Set the ContentId of [LinkedResource](https://apireference.aspose.com/java/email/com.aspose.email/linkedresource) using the [setContentId()](https://apireference.aspose.com/java/email/com.aspose.email/AttachmentBase#setContentId\(java.lang.String\)) method and passing the CID as a parameter.
1. Add the [LinkedResource](https://apireference.aspose.com/java/email/com.aspose.email/linkedresource) to the message’s [LinkedRecourceCollection](https://apireference.aspose.com/java/email/com.aspose.email/LinkedResourceCollection) collection using the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [getLinkedResources.Add()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#getLinkedResources\(\)) method.
1. Call the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [save()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) method to save the message to disk in various formats like MSG, EML, MHT.

|![todo:image_alt_text](http://i.imgur.com/E0tpRCT.png)|
| :- |
|**Figure: Output file, showing an embedded image**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-AddEmbeddedImagesToEmailMessage-.java" >}}
### **Removing Embedded Objects from Email**
[LinkedRecourceCollection](https://apireference.aspose.com/java/email/com.aspose.email/LinkedResourceCollection) accessed via [MailMessage.LinkedResources](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#getLinkedResources\(\)) property that provides a method to completely remove embedded objects added into an email message. Use the overloaded version of [LinkedResourceCollection.RemoveAt](https://apireference.aspose.com/java/email/com.aspose.email/LinkedResourceCollection#removeAt\(int,%20boolean\)) method to remove all traces of an embedded object from the email message.

The sample code below shows how to remove embedded objects from email message.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RemoveLRTracesFromMessageBody-RemoveLRTracesFromMessageBody.java" >}}
### **Extracting Embedded Objects**
Sometimes, we get emails with other emails embedded in them as attachments. These embedded emails are complete messages with their own recipient list, subject, body, and even attachments. Each of these messages can also contain embedded messages.

Using Aspose.Email for Java, developers can access each embedded message as an individual message. This example demonstrates reading embedded messages from emails.

To read attachments embedded into an email message:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class.
1. Load the existing email message using the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class' [load()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#load\(java.io.InputStream\)) method, specifying the correct [MessageFormat](https://apireference.aspose.com/java/email/com.aspose.email/messageformat).
1. Call the *Recursive* method by passing the instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class as a parameter.
1. Iterate over [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) instance's attachment collection.
1. Replace invalid characters from the attachment name and restrict the name to 50 chars.
1. Save the attachment to disk using the [Attachment](https://apireference.aspose.com/java/email/com.aspose.email/attachment) class' [save()](https://apireference.aspose.com/java/email/com.aspose.email/AttachmentBase#save\(java.io.OutputStream\)) method.
1. Repeat 1 – 6.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadEmbeddedEmailAttachmentsFromMessage-.java" >}}
#### **Identify and Extract embedded attachment from MSG formatted as RTF**
Email messages with an RTF formatted body may contain inline attachments that are either embedded as a whole object or as an icon. In order to differentiate between these two types of attachments, certain properties of the attachment need to be investigated first. After meeting certain criteria based on the attachment properties, the attachment can be saved by extracting it from its ObjectData. This article identifies and extracts embedded attachment from MSG file formatted as RTF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExtractMSGEmbeddedAttachments-ExtractMSGEmbeddedAttachments.java" >}}
