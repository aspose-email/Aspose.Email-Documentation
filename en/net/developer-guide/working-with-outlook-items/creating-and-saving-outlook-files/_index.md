---
title: Creating and Saving Outlook Files
ArticleTitle: Creating and Saving Outlook Files
type: docs
weight: 10
url: /net/creating-and-saving-outlook-files/
---

Aspose.Email supports creating Outlook message (MSG) files. This article explains how to:

- [**Create and Save Outlook Messages**](#create-and-save-outlook-messages)
- [**Create MSG Files With Attachments**](#create-msg-files-with-attachments)
- [**Create MSG Files with RTF Body**](#create-msg-files-with-rtf-body)
  - [**RTF Compression for MAPI Message Body**](#rtf-compression-for-mapi-message-body)
- [**Save Message in Draft Status**](#save-message-in-draft-status)
  
## **Create and Save Outlook Messages**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class has the [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) method that can save Outlook MSG files to disk or stream. The code snippets below create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, set properties like from, to, subject and body. The [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) method takes the file name as an argument. In addition, the Outlook Messages can be created with a [compressed RTF body]([/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody)) using the [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/). To set up, create a new Windows application and add a reference to the Aspose.Email dll into the project.

1. Create a new instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class and set the From, To, Subject and Body properties.
2. Call the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) method which accepts the object of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) type. The [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) method converts the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) (MSG).
3. Call the [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save/) method to save the MSG file.

Write the following code in the click event of the button control of the Windows application.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}

## **Create MSG Files With Attachments**

[In the example above](https://docs.aspose.com/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), we created a simple MSG file. Aspose.Email also supports saving message files with attachments. All you need to do is to add the attachments to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance. Add attachments by calling the *Add()* method on the [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) collection. Add a listbox to the form created above and add two buttons, one each for adding and removing attachments. The application that adds applications works like this:

1. When the **Add Attachment** button is clicked, an **Open File Dialog** is displayed to help users browse and select the attachment.
2. When a file has been selected, the full path is added to a list.
3. When the MSG file is created, the attachment paths are grabbed from the list and added to the [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachments/) collection.

Write the following code in the **Add Attachment** button click event.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}

When the **Remove Attachment** button is clicked, remove the selected items from the listbox. Write the following code in the Remove Attachment button click event.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}

Add the code for adding the attachments to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance. The final code for the Write Msg function is written as below.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}

## **Create MSG Files with RTF Body**

You can also create Outlook Message (MSG) files with rich text (RTF) bodies with Aspose.Email. The RTF body supports text formatting. Create one by setting the [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) property. When you convert a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) instance, the HTML body is converted into RTF. This way, the formatting of the email body is preserved.

The following example creates an MSG file with an RTF body. There is one heading, bold and underline formatting applied in the HTML body. This formatting is retained when the HTML is converted into RTF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}

### **RTF Compression for MAPI Message Body**

> **_NOTE:_** The compression process can slow down performance when creating messages. By understanding this fact and configuring the compression flag based on specific requirements and compromise between the file size and performance, developers can effectively manage the creation of MSG and PST files when dealing with email messages.

RTF compression is intended to reduce the size of a message as well as the resulting PST (Personal Storage Table) files that Microsoft Outlook uses to store e-mail messages and other data. By using RTF compression when configuring the message body, developers can reduce the amount of memory needed to store e-mail messages or optimize network bandwidth when transmitting messages.

For this purpose, there have been designed two overloaded methods:

- [MapiMessageItemBase.SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodycontent/)(string content, BodyContentType contentType, bool compression): This method lets you set the message body content using the specified string content and specifying the body contentType (for example, plain text, HTML, etc.). The optional compression parameter is a value that specifies whether the content should be compressed using RTF compression. If the compression parameter is true, the content will be compressed, resulting in a smaller message size.

- [MapiMessageItemBase.SetBodyRtf](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/setbodyrtf/)(string content, bool compression): This method specifically sets the content of the message body in RTF format. The content parameter is a string representing the RTF content that will be set as the message body. As in the previous method, the compression parameter determines whether RTF compression should be applied to the content. If compression is true, the RTF content will be compressed to reduce the size.

The following code sample shows how to set html body and keep it compressed:

```cs
var msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.SetBodyContent(htmlBody, BodyContentType.Html, true);
```

There is also a [MapiConversionOptions.UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/) property. When this property is enabled, RTF body compression is applied during MailMessage to MapiMessage conversion, resulting in a smaller MSG file size. It is shown in the code sample below:

```cs
var message = MailMessage.Load(fileName);
var options = new MapiConversionOptions();
options.UseBodyCompression = true;
var msg = MapiMessage.FromMailMessage(message, options);
```

## **Save Message in Draft Status**

Emails are saved as drafts when someone has started editing them but wants to return to them to complete them later. Aspose.Email supports saving email messages in draft status by setting a message flag. Below is the sample code to save an Outlook email message (MSG) as a draft.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}


