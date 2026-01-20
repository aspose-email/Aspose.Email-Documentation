---
title: Outlook Templates, Signed Messages & Categories in C++
ArticleTitle: Manage Outlook Templates, Signed Messages & Categories 
linktitle: Outlook Templates, Signed Messages & Categories in C++
type: docs
weight: 30
url: /cpp/manage-outlook-templates-signed-messages-categories/
description: Learn how to load and modify Outlook templates (OFT), preserve digital signatures, manage color categories, and access follow-up data in C++.
---

## **Read and Write Outlook Template (OFT) Files**

**Outlook templates** are reusable email files (.oft) that help automate sending similar or recurring messages. Instead of rewriting the same content each time, you can open a saved template, update the details, and send it instantly.

Using **Aspose.Email for C++**, you can load and modify OFT templates through the [MailMessage]() class. Once loaded, you can update fields such as sender, recipient, subject, and body, and then either:

- Send the updated message using the SmtpClient class, or
- Save it as an MSG file for further editing or validation in Microsoft Outlook.

The following code sample demonstrates how to load an Outlook email template (OFT file), modify its sender and recipient details, personalize the email content by replacing placeholders with specific values, and then save the updated message as an Outlook MSG file with the unsent flag set.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cpp" >}}

## **Manage Digitally Signed (S/MIME) Messages**


### **Preserve Signature when Converting EML to MSG**

Aspose.Email fully supports **S/MIME** operations, allowing you to save or convert digitally signed messages without breaking their signature integrity. The API provides two methods for preserving the signature when converting from EML to MSG.

**1.  Preserve S/MIME signature automatically**

1. Load the EML file with [MailMessage::Load()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a039facc73c20094aa28efd7e1b9bb647). It parses MIME structure: headers, body parts, attachments, signatures.
2. Save as MSG by calling [Save()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a7e7c6b50c8db5a8bcc6934db02b4a786) with [SaveOptions::get_DefaultMsgUnicode()](https://reference.aspose.com/email/cpp/class/aspose.email.save_options#ab61a01228ac71471841f8b2d1ff76b3f). This builds Unicode MSG format automatically while preserving the message hierarchy and content integrity.

If the original message includes an S/MIME digital signature, it is recognized and preserved as a special attachment within the resulting MSG file.

No body reformatting occurs ensuring that the signature remains valid.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cpp" >}}

**2. Controlled Conversion**

This approach uses a two-step process that explicitly converts a MIME-based message to a MAPI-based message representation.

1. Load the EML file with [MailMessage::Load()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a039facc73c20094aa28efd7e1b9bb647). It parses EML into MIME object model with headers, body parts, attachments.
2. Convert to MAPI message with [MapiMessage::FromMailMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message#a2bae96236415d510266d32f13fdc12d5).
3. Configure [MapiConversionOptions](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_conversion_options/):
    - Set output encoding (ANSI/Unicode).
    - Choose message format.
    - Preserve TNEF attachments if needed.
    - Include or preserve digital signatures.
    - Define body format (Plain text, RTF, HTML).
4. Enable `PreserveSignature = true` to keep S/MIME signature intact. This embeds the signature MIME part (application/pkcs7-mime or pkcs7-signature) without decoding or rewrapping.
5. Save resulting MAPI Message as MSG file preserving all properties and signatures.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cpp" >}}

Use this method to allow customization of message body format, encoding, and attachment handling. It is useful for converting while retaining TNEF data, managing attachments differently, or integrating MSG creation into complex Outlook/MAPI workflows. It gives access to the MAPI property set for deep-level manipulation.

## **Set Color Categories for Outlook MSG Files**

Color categories help organize emails in Outlook. Aspose.Email provides the [FollowUpManager](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_manager/) class and some functions to manage these categories:

- `AddCategory` takes [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) and the color category string, for example "Purple Category" or "Red Category" as arguments.
- `RemoveCategory` takes [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) and the color category string to be removed from the message.
- `ClearCategories()` is used to remove all the color categories from the message.
- `GetCategories` is used to retrieve all the color categories from a particular message.

The following code sample demonstrates how to load an Outlook MSG email file, add color categories to the message, retrieve and display its existing categories, and then remove specific categories or clear all categories using the [FollowUpManager](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.follow_up_manager/).

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetColorCategories-SetColorCategories.cpp" >}}

## **Access Follow-Up Information in MSG Files**

Aspose.Email can extract **read receipts**, **delivery receipts**, and **voting results** from Outlook messages.

The following code sample demonstrates how to read an Outlook MSG file and iterate through its recipients to display detailed tracking information. Specifically, it shows how to access each recipient's display name, the delivery time of the message to that recipient, and the time when the recipient read the message by retrieving these properties from the recipient properties of the MAPI message.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cpp" >}}
