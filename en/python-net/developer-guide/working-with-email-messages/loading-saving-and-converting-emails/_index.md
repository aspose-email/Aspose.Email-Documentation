---
title: Loading, Saving and Converting Emails 
ArticleTitle: Loading, Saving and Converting Emails
type: docs
weight: 30
url: /python-net/loading-saving-converting-emails/
---


## **Detecting Email File Formats**

Aspose.Email API provides the capability to detect file format of the provided message file. The [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1) method of [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/#fileformatutil-class) class can be used to achieve this. The following classes and methods can be used to detect the loaded file format:

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Class [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Class [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Method detect_file_format(stream)
- Method detect_file_format(file_path)

The following code snippet shows you how to detect file formats:

```py
from aspose.email.tools import FileFormatUtil

# Detect file format and get the detected load format
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("The message format is: " + str(info.file_format_type))
```

## **Loading a Message with Load Options**

The following code snippet shows you how to load a message with load options.

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions

# Load Eml, html, mhtml, msg, and dat files
mail_message = MailMessage.load(data_dir + "message.eml", EmlLoadOptions())
MailMessage.load(data_dir + "description.html", HtmlLoadOptions())
MailMessage.load(data_dir + "message.mhtml", MhtmlLoadOptions())
MailMessage.load(data_dir + "message.msg", MsgLoadOptions())

# Loading with custom options
eml_load_options = EmlLoadOptions()
eml_load_options.preferred_text_encoding = "utf-8"
eml_load_options.preserve_tnef_attachments = True

MailMessage.load(data_dir + "description.html", eml_load_options)

html_load_options = HtmlLoadOptions()
html_load_options.preferred_text_encoding = "utf-8"
html_load_options.should_add_plain_text_view = True
html_load_options.path_to_resources = data_dir

MailMessage.load(data_dir + "description.html", html_load_options)
```

### **Preserving Embedded Message Format during Loading**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Embedded message file format: " + str(file_format))
```

## **Saving and Converting Emails**

Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) and the classes [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) can be used for additional settings when saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.

### **Saving as EML**

The following code snippet shows you how to load an EML message and save it to the disc in the same format.

```py
from aspose.email import MailMessage, SaveOptions

# Initialize and Load an existing EML file by specifying the MessageFormat
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```

### **Preserving Boundaries in EML Files**

The following code snippet shows you how to load an EML file and save it in the same format preserving the original boundaries.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved original boundaries
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```

### **Customize MIME Boundary Strings**

Aspose.Email for .NET allows you to configure the boundary template used in MIME messages. This is achieved through the `boundaries_template` property of the [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/#emlsaveoptions-class) class.

By setting a custom template, you can define how MIME boundaries are generated. The {#} wildcard in the template will be replaced with an incremental boundary number, enabling dynamic and readable boundary strings.

If `boundaries_template` is not set (default is None), the library uses its internal boundary format.

The following code sample shows how to customize the MIME boundary strings when saving an email message to the .eml format:

```py
import aspose.email as ae

# Create a sample MailMessage
message = ae.MailMessage()
message.subject = "Custom MIME Boundary"
message.body = "This message uses a custom MIME boundary template."
message.to.append(ae.MailAddress("recipient@example.com"))

# Configure save options with a custom boundary template
save_options = ae.EmlSaveOptions(ae.MailMessageSaveType.EML_FORMAT)
save_options.boundaries_template = "boundary--{#}"

# Save the message to .eml with custom boundaries
message.save("Custom_Boundary_Message.eml", save_options)
```

Here is an **example of the message structure** with custom boundares saved using the code shown above:

```
From: sender@example.com  
To: recipient@example.com  
Subject: Custom_Boundary_Message  
Date: Fri, 27 Dec 2024 12:00:00 +0000
Content-Type: multipart/mixed;
 boundary="boundary--1"

This is a multi-part message in MIME format.

--boundary--1
Content-Type: multipart/alternative; boundary="boundary--2"


--boundary--2
Content-Type: text/plain; charset="utf-8"
Content-Transfer-Encoding: quoted-printable

Content-Type: text/plain; charset="us-ascii"

This is the plain text content of the email.


--boundary--2
Content-Type: text/html; charset="windows-1251"
Content-Transfer-Encoding: quoted-printable

<html>
  <body>
    <p>This is the <b>HTML</b> content of the email.</p>
  </body>
</html>

--boundary--2--

--boundary--1
Content-Type: application/octet-stream; name="report-2023-08.xlsx"
Content-Transfer-Encoding: base64
Content-Disposition: attachment; filename="report-2023-08.xlsx"

UEsDBBQABgAIAAAAIQBi7...

--boundary--1--
```


### **Preserving TNEF Attachments in EML Files**

The following code snippet shows you how to save an EML file preserving TNEF attachments.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved attachment
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```

### **Saving as MSG**

The following code snippet shows you how to load an EML message and convert it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save the Email message to disk in ASCII format and Unicode format
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```

### **Preserving Dates in MSG Files**

The [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) class allows you to save the source message as an Outlook Message file (MSG) preserving dates. The following code snippet shows you how to save an EML file as MSG and preserve dates.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save as msg with preserved dates
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```

### **Saving as MHTML**

Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to load an EML message into [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) and convert it to MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```

#### **Custom MHTML Conversion Settings**

The [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) class provides additional options for saving email messages to MHTML format. The enumerator [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) makes it possible to write additional email information to the output MHTML. The following additional fields can be written:

 - NONE - No specific settings are specified.
 - WRITE_HEADER - Indicates that header information should be written.
 - WRITE_OUTLINE_ATTACHMENTS - Indicates that outline attachments should be written.
 - WRITE_COMPLETE_EMAIL_ADDRESS - Indicates that complete e-mail address should be written in all email headers.
 - NO_ENCODE_CHARACTERS - Indicates that no transfer encoding of characters should be used.
 - HIDE_EXTRA_PRINT_HEADER - Indicates that PageHeader will be unvisible.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS - Indicates that complete e-mail address should be written in ‘To’ header.
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS - Indicates that complete e-mail address should be written in ‘From’ header.
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS - Indicates that complete e-mail address should be written in ‘Cc’ header.
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS - Indicates that complete e-mail address should be written in ‘Bcc’ header.
 - RENDER_CALENDAR_EVENT - Indicates that text from calendar event should be written in output mhtml.
 - SKIP_BYTE_ORDER_MARK_IN_BODY - Indicates that Byte Order Mark (BOM) bytes should be written to body.
 - RENDER_V_CARD_INFO - Indicates that text from VCard AlternativeView should be written in output mhtml.
 - DISPLAY_AS_OUTLOOK - Indicates that From header will be displayed as in Outlook.
 - RENDER_TASK_FIELDS - Indicates that the specific Task fields should be written in output mhtml.

The following code snippet shows you how to convert an EML file to MHTML with optional settings.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MailMessageSaveType, FileCompatibilityMode

# Load an existing EML file
eml = MailMessage.load(data_dir + "message.eml")

# Save as mht with header
mht_save_options = MhtSaveOptions()

# Specify formatting options required
# Here we are specifying to write header information to output without writing extra print header
# and the output headers should be displayed as the original headers in the message
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.HIDE_EXTRA_PRINT_HEADER | MhtFormatOptions.DISPLAY_AS_OUTLOOK

# Check the body encoding for validity.
mht_save_options.check_body_content_encoding = True

eml.save(data_dir + "outMessage_out.mht", mht_save_options)
```

#### **Including Calendar Events in MHTML Conversion**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) renders the Calendar events to the output MHTML.
The following code snippet shows you how to render calendar events while converting to MHTML:

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

file_name = "message.msg"

# Load the MSG file
msg = MailMessage.load(data_dir + file_name)

# Create MHT save options
options = MhtSaveOptions()
options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.RENDER_CALENDAR_EVENT

# Save the message as MHTML
msg.save(data_dir + "Meeting with Recurring Occurrences.mhtml", options)
```

#### **Exporting Email to MHT without Inline Images**

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

# Load the EML file
eml = MailMessage.load(data_dir + "message.eml")

# Create MHT save options
mht_save_options = MhtSaveOptions()
mht_save_options.skip_inline_images = True

# Save the message as MHTML without inline images
eml.save(data_dir + "EmlToMhtmlWithoutInlineImages_out.mht", mht_save_options)
```

#### **Exporting Email to MHT with Custom Time Zone**

[MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class provides the [TimeZoneOffset](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#properties) property to set customized time zone while exporting to MHT. The following code snippet shows you how to export an email to MHT with customized time zone:

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode
from datetime import timedelta

# Load the EML file
eml = MailMessage.load(data_dir + "message.eml")

# Set the local time for message date
eml.time_zone_offset = timedelta(hours=-8)

# The dates will be rendered by the local system time zone
mht_save_options = MhtSaveOptions()
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER
eml.save(data_dir + "ExportEmailToMHTWithCustomTimezone_out.mhtml", mht_save_options)
```

### **Saving as HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) class allows you to export the message body to HTML with the option to save embedded resources. The following code snippet shows you how to save a message as HTML where the default value of embed_resources is true.

```py
from aspose.email import MailMessage, SaveOptions, HtmlSaveOptions, HtmlFormatOptions

# Load the EML file
message = MailMessage.load(data_dir + "message.eml")

# Save the Email message as HTML
message.save(data_dir + "SaveAsHTML_out.html", SaveOptions.default_html)

# OR

eml = MailMessage.load(data_dir + "message.eml")
options = HtmlSaveOptions()
options.embed_resources = False
options.html_format_options = (
    HtmlFormatOptions.WRITE_HEADER
    | HtmlFormatOptions.WRITE_COMPLETE_EMAIL_ADDRESS
)  # save the message headers to output HTML using the formatting options
eml.save(data_dir + "SaveAsHTML1_out.html", options)
```

### **Saving as Outlook Template (.OFT)**

The following code snippet shows you how to save a message as an Outlook template (.oft) file.

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "template subject", "Template body")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```
