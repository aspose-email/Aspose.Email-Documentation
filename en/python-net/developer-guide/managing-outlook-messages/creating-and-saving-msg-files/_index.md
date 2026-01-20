---
title: Creating and Saving MSG files
ArticleTitle: Creating and Saving MSG files
type: docs
weight: 10
url: /python-net/creating-and-saving-msg-files/
---


Aspose.Email supports creating Outlook message (MSG) files. This article explains how to:

- Create MSG.
- Create MSG with attachments.
- Create MSG with RTF body.
- Save a message as draft.
- Work with body compression.

## **Create and Save Outlook Messages**

The [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class has the [Save()](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#methods) method that can save Outlook MSG files to a disk or a stream. The code snippet below shows how to create and save an Outlook message file:

1. Initialize a MailMessage object `eml` using the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class.
2. Set email properties like from, to, subject and body.
3. Convert the `eml` object to `outlookMsg` using the [MapiMessage.from_mail_message()](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method.
4. Call the [MapiMessage.Save()](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method to save the `outlookMsg` as an MSG file with the name "CreatingAndSavingOutlookMessages_out.msg" in the directory specified by `dataDir`.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookMSG-CreatingAndSavingOutlookMSG.py" >}}

## **Add Attachments to MSG Files**

In the example above, we created a simple MSG file. Aspose.Email also supports saving message files with attachments. All you need to do is to add the attachments to the MailMessage instance. Add attachments by calling the [add_attachment](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#methods) method on the [MailMessage.Attachments](https://reference.aspose.com/email/python-net/aspose.email/attachmentcollection/#attachmentcollection-class) collection. The code snippet below demonstrates how to create and configure an email message, add attachments, and then save it as an MSG file.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingMSGAttachments-AddingMSGAttachments.py" >}}


## **Create MSG Files with RTF Body**

You can also create Outlook Message (MSG) files with rich text (RTF) bodies with Aspose.Email. The RTF body supports text formatting. Create one by setting the [MailMessage.html_body](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#properties) property. When you convert a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) instance into a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) instance, the HTML body is converted into RTF. This way, the formatting of the email body is preserved.

The following code snippet demonstrates how to create an Outlook MSG file with a Rich Text Format (RTF) body:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingMSGFilesWithRtfBody-CreatingMSGFilesWithRtfBody.py" >}}

## **Save Messages in Draft Status**

When someone starts composing an email but isn't ready to send it, they can save it as a draft for later completion. This allows them to return and finish editing the email at a more convenient time. Aspose.Email supports saving email messages in draft status by setting a message flag. Below is the sample code to save an Outlook email message (MSG) as a draft.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SavingMessageInDraftStatus-SavingMessageInDraftStatus.py" >}}

## **Understand Body Compression in Outlook Messages**

The RTF body compression method can be used to generate a smaller size MSG. However, this results in slower speed. To create messages with improved speed, set the [use_body_compression](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#properties) flag to false. This flag, in turn, affects the created PSTs: smaller MSG files result in a smaller PST, and larger MSG files lead to slower PST creation.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetBodyCompression-SetBodyCompression.py" >}}



