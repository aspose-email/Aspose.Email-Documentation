---
title: Creating and Saving MSG Files
type: docs
weight: 10
url: /net/creating-and-saving-msg-files/
---


Aspose.Email supports creating Outlook message (MSG) files. This article explains how to:

- Create MSG messages.
- Create MSG messages with attachments.
- Create a MSG message with an RTF body.
- Save a message as a draft.
- Work with body compression.
## **Creating and Saving Outlook Messages**
The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class has the [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) method that can save Outlook MSG files to disk or stream. The code snippets below create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class, set properties like from, to, subject and body. The [Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) method takes the file name as an argument. In addition, the Outlook Messages can be created with a [compressed RTF body](/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingmsgfileswithrtfbody) using the [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions). To set up, create a new Windows application and add a reference to the Aspose.Email dll into the project.

1. Create a new instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class and set the From, To, Subject and Body properties.
1. Call the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) class [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/frommailmessage/index) method which accepts the object of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) type. The [FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/frommailmessage/index) method converts the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) (MSG).
1. Call the [MapiMessage.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/save/index) method to save the MSG file.

Write the following code in the click event of the button control of the Windows application.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookMessages-CreatingAndSavingOutlookMessages.cs" >}}
## **Creating MSG Files With Attachments**
[In the example above](/email/net/managing-message-files-with-aspose-email-outlook/#managingmessagefileswithaspose-email-outlook-creatingandsavingoutlookmessages), we created a simple MSG file. Aspose.Email also supports saving message files with attachments. All you need to do is to add the attachments to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance. Add attachments by calling the *Add()* method on the [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/attachments) collection. Add a listbox to the form created above and add two buttons, one each for adding and removing attachments. The application that adds applications works like this:

1. When the **Add Attachment** button is clicked, an **Open File Dialog** is displayed to help users browse and select the attachment.
1. When a file has been selected, the full path is added to a list.
1. When the MSG file is created, the attachment paths are grabbed from the list and added to the [MailMessage.Attachments](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/attachments) collection.

Write the following code in the **Add Attachment** button's click event.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-CreateMessagesWithAttachments.cs" >}}



When the **Remove Attachment** button is clicked, remove the selected items from the listbox. Write the following code in the Remove Attachment button's click event.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-RemoveAttachment.cs" >}}



Add the code for adding the attachments to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance. The final code for the Write Msg function is written as below.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-WorkingWithMSGAttachments-AddingMSGAttachments.cs" >}}
## **Creating MSG Files With RTF Body**
You can also create Outlook Message (MSG) files with rich text (RTF) bodies with Aspose.Email. The RTF body supports text formatting. Create one by setting the [MailMessage.HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/htmlbody) property. When you convert a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) instance, the HTML body is converted into RTF. This way, the formatting of the email body is preserved.

The following example creates an MSG file with an RTF body. There is one heading, bold and underline formatting applied in the HTML body. This formatting is retained when the HTML is converted into RTF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingMSGFilesWithRTFBody-CreatingMSGFilesWithRTFBody.cs" >}}
## **Saving Message in Draft Status**
Emails are saved as drafts when someone has started editing them but wants to return to them to complete them later. Aspose.Email supports saving email messages in draft status by setting a message flag. Below is the sample code to save an Outlook email message (MSG) as a draft.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingMessageInDraftStatus-SavingMessageInDraftStatus.cs" >}}
## **Implications of Body Compression**
The RTF body compression method can be used to generate a smaller size MSG. However, this results in slower creation speed. To create messages with improved speed, set the flag to **false**. This flag, in turn, has an effect on the created PSTs: smaller MSG files result in smaller PST, and large MSG files result in slower PST creation.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetBodyCompression-SetBodyCompression.cs" >}}
