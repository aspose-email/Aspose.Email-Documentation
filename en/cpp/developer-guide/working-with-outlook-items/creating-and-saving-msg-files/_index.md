---
title: Creating and Saving Outlook MSG files using C++ Email API
ArticleTitle: Creating and Saving Outlook MSG files using C++ Email API
linktitle: Creating and Saving MSG files
type: docs
weight: 10
url: /cpp/creating-and-saving-msg-files/
description: C++ Email Parser API supports creating Outlook message MSG files with attachments, RTF body, and save message in draft status.
---

## **Creating and Saving MSG Files**
Aspose.Email supports creating Outlook message (MSG) files. This article explains how to:

- Create MSG messages.
- Create MSG messages with attachments.
- Create a MSG message with an RTF body.
- Save a message as draft.
- Work with body compression.

### **Creating and Saving Outlook Messages**
The MailMessage class has the Save() method that can save Outlook MSG files to disk or stream. The code snippets below create an instance of the MailMessage class, set properties like from, to, subject and body. The Save() method takes the file name as an argument. In addition, the Outlook Messages can be created with a compressed RTF body using the MapiConversionOptions. To set up, create a new Windows application and add a reference to the Aspose.Email dll into the project.

1. Create a new instance of the MailMessage class and set the From, To, Subject and Body properties.
1. Call the MailMessage class FromMailMessage method which accepts object of the MailMessage type. The FromMailMessage() method converts the MailMessage into a MailMessage (MSG).
1. Call the MapiMessage.Save() method to save the MSG file.

Write the following code in the click event of the button control of the Windows application.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cpp" >}}

### **Creating MSG Files With RTF Body**
You can also create Outlook Message (MSG) files with rich text (RTF) bodies with Aspose.Email. The RTF body supports text formatting. Create one by setting the MailMessage.HtmlBody property. When you convert a MailMessage instance into a MailMessage instance, the HTML body is converted into RTF. This way, the formatting of the email body is preserved.

The following example creates an MSG file with an RTF body. There is one heading, bold and underline formatting applied in the HTML body. This formatting is retained when the HTML is converted into RTF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cpp" >}}

### **Saving Message in Draft Status**
Emails are saved as drafts when someone has started editing them but wants to return to them to complete them later. Aspose.Email supports saving email message in draft status by setting a message flag. Below is the sample code to save an Outlook email message (MSG) as a draft.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cpp" >}}

### **Implications of Body Compression**
The RTF body compression method can be used to generate a smaller size MSG. However, this results in slower speed. To creating messages with improved speed, set the flag to false. This flag, in turn, has effect on the created PSTs: smaller MSG files results in smaller PST, and large MSG files returns in slower PST creation.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetBodyCompression-SetBodyCompression.cpp" >}}

