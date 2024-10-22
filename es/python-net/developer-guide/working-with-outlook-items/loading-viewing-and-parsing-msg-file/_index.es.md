---
title: "Cargando, Visualizando y Parseando Archivos MSG"
url: /es/python-net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---

Este tema explica cómo cargar un archivo de mensaje de Microsoft Outlook (*.msg). La clase [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) se utiliza para cargar archivos MSG y proporciona varias funciones de carga estáticas para diferentes escenarios. El siguiente fragmento de código muestra cómo cargar archivos MSG desde un archivo o desde un flujo.
{{% alert %}}
**¡Pruébalo!**

Parsea archivos de correo electrónico en línea con la gratuita [**Aspose.Email Parser App**](https://products.aspose.app/email/es/parser).
{{% /alert %}}
## **Cargando Archivos MSG**
El siguiente fragmento de código muestra cómo cargar archivos MSG.

```py
from aspose.email.mapi import MapiMessage

# Crear una instancia de MapiMessage desde un archivo
msg = MapiMessage.from_file("message.msg")

# Obtener el asunto
print("Subject: " + msg.subject)

# Obtener la dirección del remitente
print("From: " + msg.sender_email_address)

# Obtener el cuerpo
print("Body: " + msg.body)

# Obtener información de los destinatarios
recipients = ", ".join([r.email_address for r in msg.recipients])
print("Recipients: " + recipients)

# Obtener archivos adjuntos
for att in msg.attachments:
    print(att.file_name)
    print(att.display_name)
```
## **Cargando desde un Flujo**
El siguiente fragmento de código muestra cómo cargar un archivo desde un flujo.

```py
from aspose.email.mapi import MapiMessage
import io

# Leer el archivo en un arreglo de bytes
file_path = dir_path + "message.msg"
with open(file_path, "rb") as file:
    bytes_data = file.read()

# Crear un flujo de memoria a partir del arreglo de bytes
stream = io.BytesIO(bytes_data)
stream.seek(0)

# Crear una instancia de MapiMessage desde el flujo
msg = MapiMessage.from_stream(stream)

# Obtener el asunto
print("Subject: " + msg.subject)

# Obtener la dirección del remitente
print("From: " + msg.sender_email_address)

# Obtener el cuerpo
print("Body: " + msg.body)
```

## **Convirtiendo EML a MSG preservando el formato EML embebido**
Los archivos EML se pueden cargar en la clase [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) instanciando un objeto [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) y pasándolo al método MapiMessage.from_mail_message. Si el archivo EML contiene archivos EML embebidos, use MapiConversionOptions.PreserveEmbeddedMessageFormat para mantener el formato de los archivos EML embebidos. El siguiente fragmento de código muestra cómo cargar archivos EML en MapiMessage mientras se preserva el formato de los archivos EML embebidos.

```py
from aspose.email import MailMessage, EmlLoadOptions
from aspose.email.mapi import MapiMessage, MapiConversionOptions, OutlookMessageFormat

eml_file = dir_path + "message.eml"

# Cargar el archivo EML
eml_options = EmlLoadOptions()
eml = MailMessage.load(eml_file, eml_options)

# Crear MapiConversionOptions
conversion_options = MapiConversionOptions()
conversion_options.format = OutlookMessageFormat.UNICODE

# Preservar el formato del mensaje embebido
conversion_options.preserve_embedded_message_format = True

# Convertir EML a MSG con opciones
msg = MapiMessage.from_mail_message(eml, conversion_options)
```