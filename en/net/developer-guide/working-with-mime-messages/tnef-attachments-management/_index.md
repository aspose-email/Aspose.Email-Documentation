---
title: TNEF Attachments Processing in Emails Using .NET
ArticleTitle: TNEF Attachments Handling in Email Messages
type: docs
weight: 70
url: /net/tnef-attachments-management/
---

**TNEF (Transport Neutral Encapsulation Format)** is a proprietary format used by Microsoft Outlook to encapsulate rich content in attachments - most commonly stored as winmail.dat. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of the attachment. The email can then be saved as a normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments. This article also shows how to create TNEF EML files from Outlook MSG files.


## **Read a Message with TNEF Attachment**

The following code snippet shows you how to read a message preserving TNEF attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

## **Read a Message without TNEF Attachment**

The following code snippet shows you how to read a message without preserving TNEF attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}


## **Load and Save TNEF Attachments**

With Aspose.Email for .NET, you can load TNEF attachments directly into a [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) object using a file path or stream, and then save the object to TNEF format. This enables the creation of winmail.dat files or preservation of Outlook-specific formatting in email workflows.

The API provides the following  members in the [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) class:

**Load TNEF Attachments**
- static MapiAttachment [LoadFromTnef(string fileName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/loadfromtnef/#loadfromtnef_1) - Loads a TNEF attachment from a .dat file.

- static MapiAttachment [LoadFromTnef(Stream stream)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/loadfromtnef/#loadfromtnef) - Loads a TNEF attachment from a stream (e.g., MemoryStream or file stream).

**Save TNEF Attachments**
- void [SaveToTnef(string filename)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/savetotnef/#savetotnef_1) - Saves a MapiAttachment to a TNEF file.

- void [SaveToTnef(Stream stream)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/savetotnef/#savetotnef) - Saves a MapiAttachment to a stream in TNEF format.

The code sample below demonstrates how to extract a winmail.dat attachment from an email message, preserve it, and re-add it as an attachment to the message:


```cs
// message.eml contains a winmail.dat attachment, but by default, the attachment is not preserved.
var msg = MapiMessage.Load("message.eml");

var ms = new MemoryStream();
msg.Attachments[0].SaveToTnef("winmail.dat");

ms.Position = 0;
var fromtnefAttachment = MapiAttachment.LoadFromTnef(ms);
msg.Attachments.Add(fromtnefAttachment);

fromtnefAttachment = MapiAttachment.LoadFromTnef("winmail.dat");
msg.Attachments.Add(fromtnefAttachment);
```


## **Update Resources in TNEF Attachment**

The following code snippet shows you how to update resources in a TNEF attachment and preserve TNEF format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

## **Add Attachment to TNEF Message**

The following code snippet shows you how to add new attachments to the main message containing TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

## **Creating TNEF EML from MSG**

Outlook MSGs sometimes contain information such as tables and text styles that may get disturbed if these are converted to EML. Creating TNEF messages from such MSG files allows to retain the formatting and even send such messages via the email clients retaining the formatting. The [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) property is used to achieve this. The following code snippet shows you how to create TNEF EML from MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

For creating the TNEF, the following sample code can be used.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

## **Identify TNEF Format Messages**

The following code snippet shows you how to detect if a message is TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

## **Identify TNEF Format Attachments**

The [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) property allows to detect whether the message attachment is TNEF formatted message.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"Is Attachment TNEF?: {attachment.IsTnef}");
}
```

