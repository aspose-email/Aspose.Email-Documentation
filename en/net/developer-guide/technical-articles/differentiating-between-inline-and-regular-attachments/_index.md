---
title: Differentiating between Inline and Regular Attachments
ArticleTitle: Differentiating between Inline and Regular Attachments
type: docs
weight: 200
url: /net/differentiating-between-inline-and-regular-attachments/
---


It is a common scenario when an email message may contain inline images within its body as well as regular attachments associated with it. Using [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) class, the inline attachments can be extracted from the [LinkedResourceCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/linkedresources) class, while the regular attachments can be accessed/extracted with the [AttachmentCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/attachments) class of a message. However, this is different when the message is loaded using Aspose.Email.Mapi.MapiMessage class, as all the inline images and regular attachments are accessible to user in the same MapiAttachmentCollection class. Hence, it is needed to devise a method that can differentiate between an inline and a regular attachment when MapiMessage is used.
## **Using Aspose.Email to Differentiate between Inline and Regular Attachments**
This article explains how to differentiate inline attachments from regular ones using MapiMessage. In order to determine this differentiation, the body type of MapiMessage is taken into account as follow:

**Plain Text Body:**  Email messages with plain text body type need not be checked, as all attachments in such messages are always regular attachments.

**Html Body:** In case of a message with HTML body type, the attachment should not only contain PR_ATTACH_FLAGS (0x37140003) property, but also its value should be equal to 0x00000004 for inline attachments.  If this condition is met, then it further depends on the PR_ATTACH_CONTENT_LOCATION and PR_ATTACH_CONTENT_ID Tags to determine the nature of attachment. However, in the absence of PR_ATTACH_FLAGS Mapi tag, the attachment is checked for PR_ATTACH_DISPOSITION (0x3716001F or 0x3716001E) property to determine the attachment type.

**Rtf Body:** If the body is RTF, then all OLE attachments are inline attachments. The value of PR_ATTACH_METHOD for all OLE attachments is equal to 0x00000006.

The following code sample demonstrates to programatically differentiate between inline and regular attachments. The function IsInlineAttachment takes an attachment and Message BodyType as input parameters and returns true if the attachment is an Inline attachment.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-IdentifyInlineAndRegularAttachments-IdentifyInlineAndRegularAttachments.cs" >}}
