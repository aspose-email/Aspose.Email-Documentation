---
title: Create and Save Outlook MSG files using C++ Email API
ArticleTitle: Create and Save Outlook MSG files 
linktitle: Creating and Saving MSG files
type: docs
weight: 10
url: /cpp/creating-and-saving-msg-files/
description: Learn how to create, save, and customize Outlook MSG files in C++, including adding attachments, using RTF bodies, saving drafts, and managing body compression.
---


**Aspose.Email for C++** allows developers to programmatically create, modify, and save Outlook MSG files with full control over message properties and formatting. You can generate MSG messages from scratch, add attachments, use rich text (RTF) bodies, save drafts, and optimize message size using body compression options.


## **Create and Save Outlook Messages**

The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class provides the `Save()` method to save MSG files to disk or stream. You can define the sender, recipients, subject, and body, and then convert the message into the Outlook MSG format using the [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) class.

The following code sample demonstrates how to create a simple email message by setting the sender, recipient, subject, and body, then convert this email message into a MAPI message compatible with Outlook, and finally save it as an MSG file.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cpp" >}}



## **Create MSG Files with RTF Body**

Outlook messages support **Rich Text Format (RTF)** bodies that retain advanced text formatting such as bold, underline, and headings.
Aspose.Email automatically converts the `HtmlBody` of a `MailMessage` into RTF when saving as MSG, preserving all formatting.

The following code sample demonstrates how to create an email message with an HTML-formatted body, including headers and styled text, then convert this email into a MAPI Outlook message, and save it as an MSG file. This allows generating Outlook-compatible email files that preserve rich text formatting using Aspose.Email.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cpp" >}}


## **Save a Message in Draft Status**

You can mark a message as **draft** by setting the appropriate flag before saving it as MSG. Drafts can later be reopened and edited.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cpp" >}}


## **Optimizing with Body Compression**

Aspose.Email provides body compression for MSG files through the [MapiConversionOptions](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_conversion_options/) class. Enabling compression creates smaller MSG and PST files but can slightly slow down processing.

The following code sample demonstrates how to load an existing email message from a file, create conversion options with body compression enabled, and convert the loaded [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) to a [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) format using these options. This process optimizes the email body size during conversion for better handling within Outlook message files.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetBodyCompression-SetBodyCompression.cpp" >}}


* **UseBodyCompression = true** → smaller file size, slower performance.
* **UseBodyCompression = false** → faster conversion, larger output.








