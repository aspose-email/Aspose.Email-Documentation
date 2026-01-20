---
title: Load and Save Email Messages Using Aspose.Email for C++
ArticleTitle: Load and Save Email Messages Using Aspose.Email for C++
linktitle: Load and Save Email Messages 
type: docs
weight: 30
url: /cpp/load-and-save-email-messages/
description: Learn how to load and save email messages in EML, MSG, HTML, and MHTML formats using Aspose.Email for C++.
---


**Aspose.Email for C++** provides flexible options to load, save, and convert email messages in multiple formats, including EML, MSG, MHTML, and HTML. You can also customize load and save options to handle encoding, attachments, and formatting requirements.


## **Load a Message with Customized Load Options**

The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class can load messages from various formats such as EML, MSG, MHTML, and HTML using specialized load options. These options allow developers to specify encoding preferences, preserve attachments, and manage embedded resources.

The following C++ example demonstrates how to load email messages using different load options.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}


## **Save Email Messages in Different Formats**

Aspose.Email for C++ enables the conversion of messages between formats such as EML, MSG, MHTML, and HTML. Developers can use the [SaveOptions](https://reference.aspose.com/email/cpp/class/aspose.email.save_options/) class hierarchy to specify advanced saving parameters, including encoding, TNEF attachments, and boundary preservation.

Available save options include:

- `EmlSaveOptions`
- `MsgSaveOptions`
- `MhtSaveOptions`
- `HtmlSaveOptions`


### **Save Email as EML**

The following code snippet demonstrates how to load an EML message and saves it to the disc in the same format.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}

### **Preserve Original EML Boundaries**

You can preserve the original MIME boundaries when saving an EML file. 


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}

### **Preserve TNEF Attachments in EML**

The following code example demonstrates how to save an email while preserving TNEF (Transport Neutral Encapsulation Format) attachments.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}

### **Convert EML to MSG**

You can easily convert an **EML** file to an Outlook **MSG** format. The following code snippet demonstrates how to load an EML message and convert it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/cpp/class/aspose.email.save_options/) class.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}


### **Save as MHTML**

The following example demonstrates how to load an **EML** message and save it as an **MHTML** file.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}

#### **Export to MHT with Custom Time Zone**

You can set a custom or system time zone for message date fields before exporting to MHT format. The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class provides the [TimeZoneOffset](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a1a0d21796c28395e01fa9456c1f03195) property to set customized Timezone. The following code snippet shows you how to export an email to MHT with customized TimeZone.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}


### **Export Email to EML**

The following example shows how to export an email to EML format:

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}




