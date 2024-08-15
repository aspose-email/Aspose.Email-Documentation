---
title: "Carga, visualización y análisis de archivos MSG"
url: /es/python-net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


En este tema se explica cómo cargar un archivo de mensajes de Microsoft Outlook (*.msg). El [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) La clase se usa para cargar archivos MSG y proporciona varias funciones de carga estática para diferentes escenarios. El siguiente fragmento de código muestra cómo cargar archivos MSG desde un archivo o desde una transmisión.
{{% alert %}}
**¡Pruébalo!**

Analice archivos de correo electrónico en línea con la versión gratuita [**Aplicación de análisis Aspose.Email**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
## **Carga de archivos MSG**
El siguiente fragmento de código muestra cómo cargar archivos MSG.

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
## **Cargando desde Stream**
El siguiente fragmento de código muestra cómo cargar un archivo desde una transmisión.

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

## **Conversión de EML a MSG conservando el formato EML incrustado**
Los archivos EML se pueden cargar en [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) clase instanciando una [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) objeto y pasándolo al método mapiMessage.from_mail_message. Si el archivo EML contiene archivos EML incrustados, utilice mapiConversionOptions.preserveEmbeddedMessageFormat para conservar el formato de los archivos EML incrustados. El siguiente fragmento de código muestra cómo cargar archivos EML en MapiMessage conservando el formato de los archivos EML incrustados.

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
