---
title: "Загрузка, просмотр и анализ файла MSG"
url: /ru/python-net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


В этом разделе описывается, как загрузить файл сообщений Microsoft Outlook (*.msg). [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) класс используется для загрузки файлов MSG и предоставляет несколько функций статической загрузки для различных сценариев. В следующем фрагменте кода показано, как загружать файлы MSG из файла или из потока.
{{% alert %}}
**Попробуйте!**

Анализируйте файлы электронной почты онлайн бесплатно [**Приложение для парсера электронной почты Aspose.Email**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}
## **Загрузка файлов MSG**
В следующем фрагменте кода показано, как загружать файлы MSG.

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
## **Загрузка из стрима**
В следующем фрагменте кода показано, как загрузить файл из потока.

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

## **Преобразование EML в MSG с сохранением встроенного формата EML**
Файлы EML можно загружать в [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) класс путем создания экземпляра [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) объект и передача его методу MAPImessage.from_mail_message. Если файл EML содержит встроенные файлы EML, используйте MapiConversionOptions.PreserveEmbeddedMessageFormat, чтобы сохранить формат встроенных файлов EML. В приведенном ниже фрагменте кода показано, как загружать файлы EML в MapiMessage с сохранением формата встроенных файлов EML.

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
