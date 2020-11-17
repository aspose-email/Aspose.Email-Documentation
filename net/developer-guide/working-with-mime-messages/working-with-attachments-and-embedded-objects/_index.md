---
title: Working with Attachments and Embedded Objects
type: docs
weight: 20
url: /net/working-with-attachments-and-embedded-objects/
---


## **Managing Email Attachments**
An email attachment is a file that is sent along with an email message. The file may be sent as a separate message as well as a part of the message to which it is attached. The [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class is used with the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class. All messages include a body. In addition to the body, you might want to send additional files. These are sent as attachments and are represented as an instance of the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class. You can send any number of attachments but the size of the attachment is limited by the mail server. Gmail, for example, does not support file sizes greater than 10MB.
{{% alert %}}
**Try it out!**

Add or remove email attachments online with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}
### **Adding Attachment**
To attach an attachment to an email, please follow these steps:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Create an instance of the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class.
1. Load attachment into the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) instance.
1. Add the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) instance into the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance.

The following code snippet shows you how to add an attachment to an email.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddEmailAttachments-AddEmailAttachments.cs" >}}



Above, we described how to add attachments to your email message with Aspose.Email. What follows shows how to remove attachments, and display information about them on screen.
### **Removing an Attachment**
To remove an attachment, follow the steps given below:

- Create an instance of [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class.
- Load attachment in the instance of [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class.
- Add the attachment to the instance of [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
- Remove the attachments from the instance of [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class using the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class instance.

The following code snippet shows you how to remove an attachment.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RemovingAttachment-RemovingAttachment.cs" >}}
### **Displaying Attachment File Name**
To display the attachment file name, follow these steps:

1. Loop through the attachments in the email message and
   1. Save each attachment.
   1. Display each attachment's name on the screen.

The following code snippet shows you how to display an attachment file name on the screen.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DisplayAttachmentFileName-DisplayAttachmentFileName.cs" >}}
### **Extracting Email Attachments**
This topic explains how to extract an attachment from an email file. An email attachment is a file that is sent along with an email message. The file may be sent as a separate message as well as a part of the message to which it is attached. All email messages include an option to send additional files. These are sent as attachments and are represented as instances of the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class. The [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class is used with the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class to work with attachments. To extract attachments from an email message, follow these steps:

- Create an instance of the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
- Load an email file into the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance.
- Create an instance of the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class and use it in a loop to extract all attachments.
- Save the attachment and display it on screen.

|**Extracted attachments in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
The following code snippet shows you how to Extract Email Attachments.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cs" >}}
#### **Retrieving Content-Description from Attachment**
Aspose.Email API provides the capability to read attachment's Content-Description from attachment header. The following code snippet shows you how to retrieve the content description from the attachment.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RetrievContentDescriptionFromAttachment-RetrievContentDescriptionFromAttachment.cs" >}}
#### **Determining if Attachment is Embedded Message**
The following code snippet demonstrates how to determine if the attachment is an embedded message or not.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetermineAttachmentEmbeddedMessage-DetermineAttachmentEmbeddedMessage.cs" >}}
## **Working with Embedded Objects**
An embedded object is an object that was created with one application and enclosed within a document or file created by another application. For example, a Microsoft Excel spreadsheet can be embedded into a Microsoft Word report, or a video file can be embedded into a Microsoft PowerPoint presentation. When a file is embedded, rather than inserted or pasted into another document, it retains its original format. The embedded document can be opened in the original application and modified.
### **Embedding Objects into an Email**
The [LinkedResource](https://apireference.aspose.com/net/email/aspose.email/linkedresource) class is used with the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class to embed objects in your email messages. To add an embedded object, follow these steps

1. Create an instance of the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Specify the from, to and subject values in [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance.
1. Create an instance of the [AlternateView](https://apireference.aspose.com/net/email/aspose.email/alternateview) class.
1. Create an instance of the [LinkedResource](https://apireference.aspose.com/net/email/aspose.email/linkedresource) class.
1. Load an embedded object into the [LinkedResourceCollection](https://apireference.aspose.com/net/email/aspose.email/linkedresourcecollection).
1. Add the loaded embedded object into the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class instance.
1. Add the [AlternateView](https://apireference.aspose.com/net/email/aspose.email/alternateview) instance to the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class instance.

The code snippets below produce an email message with both plain text and HTML bodies and an image embedded into the HTML

|**Image embedded into email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
You can send any number of embedded objects. The size of the attachment is limited by the mail server. Gmail, for example, does not support file sizes greater than 10MB. The code snippets below demonstrate how to embed objects into an Email.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EmbeddedObjects-EmbeddedObjects.cs" >}}
### **Removing Embedded Objects from Email**
[LinkedResourceCollection](https://apireference.aspose.com/net/email/aspose.email/linkedresourcecollection) accessed via [MailMessage.LinkedResources](https://apireference.aspose.com/net/email/aspose.email/mailmessage/properties/linkedresources) property. The [LinkedResourceCollection](https://apireference.aspose.com/net/email/aspose.email/linkedresourcecollection) collection provides a method to completely remove embedded objects added into an email message. Use the overloaded version of [LinkedResourceCollection.RemoveAt](https://apireference.aspose.com/net/email/aspose.email/linkedresourcecollection/methods/removeat/index) method to remove all traces of an embedded object from an email message.

The sample code below shows how to remove embedded objects from an email message.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RemoveLRTracesFromMessageBody-RemoveLRTracesFromMessageBody.cs" >}}
### **Extracting Embedded Objects**
This topic explains how to extract embedded objects from an email file. An embedded object is an object that was created with one application and enclosed within a document or file created by another application. For example, a Microsoft Excel spreadsheet can be embedded into a Microsoft Word report, or a video file can be embedded into a Microsoft PowerPoint presentation. When a file is embedded, rather than inserted or pasted into another document, it retains its original format. The embedded document can be opened in the original application and be modified. To extract an embedded object from an email message, follow these steps:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Load an email file in the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance.
1. Create a loop and create an instance of the [Attachment](https://apireference.aspose.com/net/email/aspose.email/attachment) class in it.
1. Save the attachment and display it on screen.
1. Specify the sender and recipient address in the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance.
1. Send email using the [SmtpClient](https://apireference.aspose.com/net/email/aspose.email.clients.smtp/smtpclient) class.

The code snippet below extracts embedded objects from an email.

|**Extracted embedded objects in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
The following code snippet shows you how to Extracting Embedded Objects.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cs" >}}
#### **Identify and Extract embedded attachment from MSG formatted as RTF**
For messages formatted as RTF, the following code can be used to differentiate and extract attachments that are either Inline or appear as Icon in the message body. The following code snippet shows you how to Identify and Extract embedded attachment from MSG formatted as RTF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExtractMSGEmbeddedAttachment-ExtractMSGEmbeddedAttachment.cs" >}}
