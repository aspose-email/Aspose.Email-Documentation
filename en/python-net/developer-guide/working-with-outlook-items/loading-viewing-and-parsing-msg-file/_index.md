---
title: Loading, Viewing and Parsing MSG file
ArticleTitle: Loading, Viewing and Parsing MSG file
type: docs
weight: 20
url: /python-net/loading-viewing-and-parsing-msg-file/
---


This topic explains how to load a Microsoft Outlook Messagefile (*.msg). The [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) class is used to load MSG files, and provides several static loading functions for different scenarios. The following code snippet shows you how to load MSG files from file or from stream.
{{% alert %}}
**Try it out!**

Parse email files online with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}
## **Loading MSG Files**
The following code snippet shows you how to load MSG files.

```py
from aspose.email.mapi import MapiMessage

# Create an instance of MapiMessage from file
msg = MapiMessage.from_file("message.msg")

# Get subject
print("Subject: " + msg.subject)

# Get from address
print("From: " + msg.sender_email_address)

# Get body
print("Body: " + msg.body)

# Get recipients information
recipients = ", ".join([r.email_address for r in msg.recipients])
print("Recipients: " + recipients)

# Get attachments
for att in msg.attachments:
    print(att.file_name)
    print(att.display_name)
```
## **Loading from Stream**
The following code snippet shows you how to load file from stream.

```py
from aspose.email.mapi import MapiMessage
import io

# Read the file into a byte array
file_path = dir_path + "message.msg"
with open(file_path, "rb") as file:
    bytes_data = file.read()

# Create a memory stream from the byte array
stream = io.BytesIO(bytes_data)
stream.seek(0)

# Create an instance of MapiMessage from the stream
msg = MapiMessage.from_stream(stream)

# Get subject
print("Subject: " + msg.subject)

# Get from address
print("From: " + msg.sender_email_address)

# Get body
print("Body: " + msg.body)
```

## **Converting EML to MSG preserving embedded EML format**
EML files can be loaded into [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) class by instantiating a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) object and passing it to MapiMessage.from_mail_message method. If the EML file contains embedded EML files, use MapiConversionOptions.PreserveEmbeddedMessageFormat to retain the format of embedded EML files. The below code snippet shows how to laod EML files into MapiMessage while preserving format of embedded EML files.

```py
from aspose.email import MailMessage, EmlLoadOptions
from aspose.email.mapi import MapiMessage, MapiConversionOptions, OutlookMessageFormat

eml_file = dir_path + "message.eml"

# Load the EML file
eml_options = EmlLoadOptions()
eml = MailMessage.load(eml_file, eml_options)

# Create MapiConversionOptions
conversion_options = MapiConversionOptions()
conversion_options.format = OutlookMessageFormat.UNICODE

# Preserve Embedded Message Format
conversion_options.preserve_embedded_message_format = True

# Convert EML to MSG with options
msg = MapiMessage.from_mail_message(eml, conversion_options)
```
