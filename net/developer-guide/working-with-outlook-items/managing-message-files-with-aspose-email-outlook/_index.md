---
title: Managing Message Files with Aspose.Email.Outlook
type: docs
weight: 30
url: /net/managing-message-files-with-aspose-email-outlook/
---


## **Converting MSG to MIME message**
Aspose.Email API provides the capability of converting MSG files to MIME messages using the [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/tomailmessage) method.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}
## **Reading and Writing Outlook Template File (.OFT)**
Outlook templates are very useful when you want to send a similar email message again and again. Instead of preparing the message from scratch each time, first, prepare the message in Outlook and save it as an Outlook Template (OFT). After that, whenever you need to send the message, you can create it from the template, saving time writing the same text in the body or the subject line, setting formatting and so on. Aspose.Email’s [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class can be used to load and read an Outlook template (OFT) file. Once the Outlook template is loaded in an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class, you can update the sender, recipient, body, subject and other properties. After updating the properties:

- Send the email using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) class or
- Save the message as MSG and do further updates/validation using Microsoft Outlook.

In the code samples below, we:

1. Load the template using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Update some of the properties.
1. Save the message in MSG format.

The following code snippet shows you how to load the OFT file, updating the message and saving it in MSG format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}
### **Saving Outlook MSG file as Template**
The following code snippet shows you how to save the outlook MSG file as a template.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}
## **Managing Digitally Signed Messages**
Aspose.Email implements the complete S/MIME email object algorithm. This gives the API complete power to preserve digital signatures while converting messages between formats.
### **Preserving Signature when Converting from EML to MSG**
Aspose.Email preserves the digital signature when converting from EML to MSG. The following code snippet shows you how to converting from EML to MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}
### **Converting S/MIME Messages from MSG to EML**
Aspose.Email preserves the digital signature when converting from MSG to EML as shown in the following code snippet.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}
## **Setting Color Category for Outlook MSG Files**
A color category marks an email message for some kind of importance or category. Microsoft Outlook lets users assign color categories to differentiate emails. To handle the color category, use the [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager). It contains functions such as [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/clearcategories) and [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/addcategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) and the color category string, for example, "Purple Category" or "Red Category" as arguments.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/removecategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) and the color category string to be removed from the message.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/clearcategories) is used to remove all the color categories from the message.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/methods/getcategories) is used to retrieve all the color categories from a particular message.

The following example performs the tasks as given below:

1. Add a color category.
1. Add another color category.
1. Retrieve the list of all categories.
1. Remove all categories.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}
## **Accessing Follow Up Information form MSG file**
Aspose.Email API provides the capability to access the follow-up information from a sent or received message. It can retrieve the Read, Delivery Read Receipt and vote results information from a message file.
### **Retrieving Read and Delivery Receipt Information**
The following code snippet shows you how to retrieve read and delivery receipt information.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}
## **Creating Forward and Reply Messages**
Aspose.Email API provides the capability of creating and formatting the forward and reply messages. The [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder) and [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder) classes of the API are used to create the Reply and Forward messages respectively. A Reply or Forward message can be specified to be created using any of the modes of [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode) enum. This enum has the following values:

- **OriginalMessageAdditionMode.None** - The original message is not included in the response message.
- **OriginalMessageAdditionMode.Attachment** - The original message is included as attachment in the response message
- **OriginalMessageAdditionMode.Textpart** - The original message is included as text in the body of response message
### **Creating Reply Message**
The following code snippet shows you how to creating reply message.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}
### **Creating Forward Message**
The following code snippet shows you how to create a forward message.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}
