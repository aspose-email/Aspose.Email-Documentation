---
title: "Загрузка, просмотр и парсинг MSG файла"
url: /ru/python-net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


Эта тема объясняет, как загрузить файл сообщения Microsoft Outlook (*.msg). Класс [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) используется для загрузки MSG файлов и предоставляет несколько статических функций загрузки для различных сценариев. Следующий код демонстрирует, как загрузить MSG файлы из файла или из потока.
{{% alert %}}
**Попробуйте!**

Парсите файлы электронной почты онлайн с бесплатным приложением [**Aspose.Email Parser App**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}
## **Загрузка MSG файлов**
Следующий код демонстрирует, как загрузить MSG файлы.

```py
from aspose.email.mapi import MapiMessage

# Создайте экземпляр MapiMessage из файла
msg = MapiMessage.from_file("message.msg")

# Получить тему
print("Subject: " + msg.subject)

# Получить адрес отправителя
print("From: " + msg.sender_email_address)

# Получить тело сообщения
print("Body: " + msg.body)

# Получить информацию о получателях
recipients = ", ".join([r.email_address for r in msg.recipients])
print("Recipients: " + recipients)

# Получить вложения
for att in msg.attachments:
    print(att.file_name)
    print(att.display_name)
```
## **Загрузка из потока**
Следующий код демонстрирует, как загрузить файл из потока.

```py
from aspose.email.mapi import MapiMessage
import io

# Прочитать файл в массив байтов
file_path = dir_path + "message.msg"
with open(file_path, "rb") as file:
    bytes_data = file.read()

# Создать поток памяти из массива байтов
stream = io.BytesIO(bytes_data)
stream.seek(0)

# Создать экземпляр MapiMessage из потока
msg = MapiMessage.from_stream(stream)

# Получить тему
print("Subject: " + msg.subject)

# Получить адрес отправителя
print("From: " + msg.sender_email_address)

# Получить тело сообщения
print("Body: " + msg.body)
```

## **Конвертация EML в MSG с сохранением встроенного формата EML**
EML файлы могут быть загружены в класс [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) путем создания объекта [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) и передачи его в метод MapiMessage.from_mail_message. Если файл EML содержит встроенные EML файлы, используйте MapiConversionOptions.PreserveEmbeddedMessageFormat для сохранения формата встроенных EML файлов. Приведенный ниже код демонстрирует, как загрузить EML файлы в MapiMessage, сохраняя формат встроенных EML файлов.

```py
from aspose.email import MailMessage, EmlLoadOptions
from aspose.email.mapi import MapiMessage, MapiConversionOptions, OutlookMessageFormat

eml_file = dir_path + "message.eml"

# Загрузить EML файл
eml_options = EmlLoadOptions()
eml = MailMessage.load(eml_file, eml_options)

# Создать MapiConversionOptions
conversion_options = MapiConversionOptions()
conversion_options.format = OutlookMessageFormat.UNICODE

# Сохранить встроенный формат сообщения
conversion_options.preserve_embedded_message_format = True

# Конвертировать EML в MSG с опциями
msg = MapiMessage.from_mail_message(eml, conversion_options)
```