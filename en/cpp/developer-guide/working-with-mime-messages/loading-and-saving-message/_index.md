---
title: Loading, Saving and Converting different Email Message formats in C++
ArticleTitle: Loading, Saving and Converting different Email Message formats in C++
linktitle: Loading and Saving Message
type: docs
weight: 30
url: /cpp/loading-and-saving-message/
description: With C++ Email Parser Library, you can load, save, export and convert different email message formats e.g. EML, MSG, MHTML.
---

## **Loading a Message with Load Options**
The following code snippet shows you how to load a message with load options.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Saving and Converting Messages**
Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class SaveOptions and the classes EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions for additional settings when saving MailMessage can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.
### **Loading EML and Saving as EML**
The following code snippet shows you how to loads an EML message and saves it to the disc in the same format.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Loading EML and Saving as EML Preserving the Original Boundaries**
The following code snippet shows you how to loading EML and saving as EML preserving the original boundaries.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Saving as EML Preserving TNEF Attachments**
The following code snippet shows you how to saving as EML preserving TNEF attachments.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Loading EML, Saving to MSG**
The following code snippet shows you how to loads an EML message and converts it to MSG using the appropriate option from SaveOptions.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Saving MailMessage as MHTML**
Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to loads an EML message into [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) and converts it to MHTML.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Exporting Email to MHT with customized TimeZone**
MailMessage class provides the TimeZoneOffset property to set customized Timezone while exporting to MHT. The following code snippet shows you how to export an email to MHT with customized TimeZone.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Exporting Email to EML**
The following code snippet shows you how to export email to eml.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}




