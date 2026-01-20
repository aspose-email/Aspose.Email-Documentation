---
title: Handling TNEF Attachments in Email Messages
ArticleTitle: Handling TNEF Attachments in Email Messages
type: docs
weight: 50
url: /python-net/handling-tnef-attachments-in-email-messages/
---


## **Email Messages Containing TNEF Attachments**

Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify their contents. The email can then be saved as a normal message or to the same format, preserving these attachments. This article shows different code samples for working with messages containing TNEF attachments. It also demonstrates how to create TNEF EML files from Outlook MSG files.

### **Identifying TNEF Attachments in an Email**

The following code snippet shows you how to detect whether an email contains TNEF attachments:

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```

### **Reading Emails while Preserving TNEF Attachments**

The following code snippet shows you how to read a message and preserve TNEF attachments.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# This will Preserve the TNEF attachment as it is, file contains the TNEF attachment
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Converting MSG to TNEF**

Outlook MSGs sometimes contain information such as tables and text styles that can be corrupted when converted to EML. Creating TNEF messages from such MSG files allows you to retain the formatting and even send such messages via the email clients retaining the formatting. The [convert_as_tnef](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#properties) property is used to achieve this. The following code snippet shows you how to create TNEF email from MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

### **Creating TNEF Email**

The following sample code can be used to create an email in TNEF format:

1. Configure file options using the [MsgLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/msgloadoptions/) class.
2. Ensure that TNEF attachments in the email are preserved when loading the file by setting [options.preserve_tnef_attachments](https://reference.aspose.com/email/python-net/aspose.email/msgloadoptions/#properties) to True.
3. Use the [MailMessage.load(eml_file_name, options)](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#methods) method to load the input email file while applying the options configured earlier. This specifically ensures that the loaded email retains TNEF-related information (such as attachments or proprietary Microsoft Outlook formats).

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# The PreserveTnefAttachments option with MessageFormat.Msg will create the TNEF eml.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```

### **Detecting TNEF Messages**

The following code snippet shows you how to detect if a message is TNEF. The [original_is_tnef](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#properties) property of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) object is checked to determine if the email was originally in TNEF (Transport Neutral Encapsulation Format). If `is_tnef` evaluates to True, it means the email contains TNEF encoding, which typically occurs in emails originating from Microsoft Outlook or Exchange.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```


