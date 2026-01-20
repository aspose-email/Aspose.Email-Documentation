---
title: Handling Attachments and Embedded Objects
ArticleTitle: Handling Attachments and Embedded Objects
type: docs
weight: 40
url: /python-net/handling-attachments-and-embedded-objects/
---


## **Managing Email Attachments**

An email attachment is a computer file which is sent along with an email message. The file may be sent as a separate message as well as a part of the message to which it is attached. The [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/) class is used to manage and manipulate attached files within an email message. 

All messages include a body. In addition to the body, you might want to send additional files. These are sent as attachments and are represented as the instance of the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/) class. You can send any number of attachments but the size of the attachment is limited by the mail server. Gmail, for example, does not support file sizes greater than 10MB.
{{% alert %}}
**Try it out!**

Add or remove email attachments online with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Adding Attachments**

To attach a file to an email message, please follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
1. Create an instance of the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/) class.
1. Load attachment into the Attachment instance.
1. Add the Attachment instance into the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class instance.

The following code snippet shows you how to add an attachment to an email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AddEmailAttachments-AddEmailAttachments.py" >}}



Above, we described how to add attachments to your email message with Aspose.Email. What follows shows how to remove attachments, and display information about them on the screen.


### **Removing Attachments**

To remove an attachment, follow the steps given below:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
2. Load an attachment from a specified file path using the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/) class.
3. Add the attachment to the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) instance's attachments collection.
4. Print the count of attachments before removing any.
5. Remove the attachment from the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) instance's attachments collection.
6. Print the count of attachments after removing the attachment.

The following code snippet shows you how to remove an attachment:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemovingAttachmentFromMailMessage-RemovingAttachmentFromMailMessage.py" >}}

### **Retrieving Attachment File Names**

To display the attachment file name, follow these steps:

1. Loop through the attachments in the loaded email.  
2. For each attachment, print its name using a loop that enumerates the attachments.

The following code snippet shows you how to display an attachment file name on the screen.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayAttachmentFileName-DisplayAttachmentFileName.py" >}}

### **Extracting Attachments**

In Aspose.Email the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class is used to work with attachments. An email attachment is a computer file which is sent along with an email message. It may be sent as a separate message as well as a part of the message to which it is attached. The file is represented as an instance of the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/#attachment-class) class. To extract attachments from email messages, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class.
2. Load an email file into the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) instance.
3. Create an instance of the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/#attachment-class) class and use it in a loop to extract all attachments.
4. Save the attachment and display it on screen.
5. Specify sender and recepient address in the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) instance.
6. Now you can send email using the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class.

The following code snippet shows you how to extract email attachments:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}

|**Extracted attachments in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|


#### **Retrieving Content-Description from Attachments**

Aspose.Email API provides the capability to read Content-Description from attachment headers. The following code snippet shows you how to retrieve content description from an attachment:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RetrievContentDescriptionFromAttachment-RetrievContentDescriptionFromAttachment.py" >}}

#### **Identifying Embedded Message Attachments**

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DetermineAttachmendEmbeddedMessage-DetermineAttachmendEmbeddedMessage.py" >}}

## **Working with Embedded Objects**

An embedded object is an object that was created with one application and embedded in a document or a file created with another application. For example, a Microsoft Excel spreadsheet can be embedded in a Microsoft Word report, or a video file can be embedded in a Microsoft PowerPoint presentation. When a file is embedded, rather than inserted or pasted into another document, it retains its original format. The embedded document can be opened in the original application and modified.

### **Extracting Embedded Objects**

The following code sample demonstrates how to extract embedded objects from an email file using Aspose.Email for Python via .NET. 

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
1. Load an email file in the MailMessage instance.
1. Create a loop and an instance of the [Attachment](https://reference.aspose.com/email/python-net/aspose.email/attachment/) class in it.
1. Save the attachment and display it on screen.
1. Specify sender and recepient address in the MailMessage instance.
1. Send email using the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/) class.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}


|**Extracted embedded objects in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|









