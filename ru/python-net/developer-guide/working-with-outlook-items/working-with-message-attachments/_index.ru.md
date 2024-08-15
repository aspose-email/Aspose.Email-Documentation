---
title: "Работа с вложениями сообщений"
url: /ru/python-net/working-with-message-attachments/
weight: 70
type: docs
---


## **Управление вложениями с помощью Aspose Outlook**
В разделе Создание и сохранение файлов сообщений Outlook (MSG) объясняется, как создавать и сохранять сообщения, а также файлы MSG с вложениями. В этой статье объясняется, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Доступ к вложениям из файла сообщений и их сохранение на диск осуществляется с помощью свойства «Вложения класса MapiMessage». Свойство «Вложения» представляет собой набор типов класса MapiAttachmentCollection.

### **Проверьте, является ли вложение встроенным или обычным**

Под «встроенными» и «обычными» вложениями понимается способ их включения в сообщение электронной почты. **Regular** вложения — это файлы, прикрепленные традиционным способом. Обычно они отображаются в виде списка в почтовом клиенте и могут быть загружены получателем и сохранены в локальном хранилище. **Inline** вложения, также известные как встроенные или встроенные изображения, обычно используются для включения изображений или других медиафайлов в текст электронного письма. Они не отображаются в отдельном списке, а отображаются непосредственно в содержимом письма, например в тексте письма. Это позволяет добавлять изображения или другие медиафайлы, которые являются частью содержимого сообщения. В приведенном ниже примере кода показано, как определить, является ли вложение встроенным или обычным:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Сохранить вложения из файла сообщений Outlook (MSG)**

Чтобы сохранить вложения из файла MSG, выполните следующие действия:

1. Просмотрите коллекцию MapiAttachmentCollection и получите отдельные вложения.
1. Чтобы сохранить вложения, вызовите метод Save () класса MapiAttachment.

В следующем фрагменте кода показано, как сохранять вложения на локальный диск.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Create an instance of MapiMessage from file
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Iterate through the attachments collection
for attachment in message.attachments:
    # Save the individual attachment
    attachment.save(data_dir + attachment.file_name)
```

### **Получение вложений вложенных почтовых сообщений**

Встроенные вложения OLE также отображаются в коллекции вложений класса MapiMessage. В следующем примере кода файл сообщений анализируется на наличие вложенных сообщений и сохраняется на диске. Статический метод класса MapiMessage FromProperties () позволяет создать новое сообщение из встроенного вложения. В следующем фрагменте кода показано, как получать вложенные вложения в почтовые сообщения.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Create a MapiMessage object from the individual attachment
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Create an object of type MailMessageInterpreter from the above message and save the embedded message to a file on disk
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Удаление вложений**

Библиотека Aspose Outlook предоставляет возможность удаления вложений из файлов сообщений Microsoft Outlook (.msg):

- Вызовите метод removeAttachments (). В качестве параметра он принимает путь к файлу сообщения. Он реализован как публичный статический метод, поэтому вам не нужно создавать экземпляр объекта.

В следующем фрагменте кода показано, как удалить вложения.


```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

Можно также вызвать статический метод класса MapiMessage DestoryAttachment (). Он работает быстрее, чем removeAttachment (), поскольку метод removeAttachment () анализирует файл сообщения.

```py
import aspose.email as ae

# Destroy attachments in the MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Добавление вложений MSG**

Сообщение Outlook может содержать другие сообщения Microsoft Outlook во вложениях в виде обычных или встроенных сообщений. MapiAttachmentCollection предоставляет перегруженным участникам метода Add возможность создавать сообщения Outlook с обоими типами вложений.
{{% alert %}}
**Попробуйте!**

Добавляйте или удаляйте вложения электронной почты онлайн бесплатно [**Приложение для редактирования электронной почты Aspose.Email**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавить справочное вложение в MAPImessage**

«Справочное вложение» обычно означает вложение, содержащее ссылку или ссылку на внешний ресурс, а не сам файл. Эти ссылки часто используются в электронных письмах в формате HTML для ссылок на внешние изображения или ресурсы, размещенные на удаленном сервере. Вместо встраивания всего файла во вложении ссылки содержится URL-адрес или ссылка на внешнее содержимое.

Aspose.Email предоставляет набор инструментов для корректного отображения справочных вложений, представленный в следующем примере кода:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Add reference attachment
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# Also, you can set additional attachment properties
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Finally save the message
msg.save("msg_with_ref_attach.msg")
```
### **Вставить сообщение в виде вложения**
В следующем фрагменте кода показано, как файлы Outlook MSG, встроенные в файл MSG, содержат метод PR_ATTACH_METHOD, значение которого равно 5.

```py
import aspose.email as ae

# Create a new MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "This is a message body")

# Load the attachment message
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Add the attachment to the message
message.attachments.add("Weekly report.msg", attach_msg)

# Save the message with the embedded message attachment
message.save("WithEmbeddedMsg_out.msg")
```
### **Чтение встроенных сообщений из вложений**
В следующем фрагменте кода показано, как прочитать встроенное сообщение из вложения.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.from_file(file_name)

# Check if the first attachment is an Outlook message
if message.attachments[0].object_data.is_outlook_message:
    # Get the embedded message as MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Perform further operations with the embedded message
    # ...
```
## **Установка и замена навесного оборудования**
Aspose.Email API предоставляет возможность вставлять вложения в определенном индексе в родительское сообщение. Он также предоставляет возможность заменять содержимое вложения другим вложением сообщения. В следующем фрагменте кода показано, как вставлять и заменять вложения.
### **Вставить в определенном месте**
API Aspose.Email предоставляет возможность вставлять вложение MSG в родительское сообщение с помощью метода вставки MapiAttachmentCollection Insert (индекс int, строковое имя, сообщение MapiMessage). В следующем фрагменте кода показано, как выполнить вставку в определенном месте.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Insert the loaded attachment at index 1
message.attachments.insert(1, "new 11", get_data)
```
### **Заменить содержимое вложения**
Это можно использовать для замены содержимого встроенного вложения новым с помощью метода Replace. Однако его нельзя использовать для вставки вложений с PR_ATTACH_NUM = 4 (например) в коллекцию с Collection.count = 2. В следующем фрагменте кода показано, как заменить содержимое вложения.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Replace the attachment at index 1 with the loaded attachment
message.attachments.replace(1, "new 1", get_data)
```
### **Переименовать вложение в MAPIMessage**

Можно изменить отображаемые имена вложений в сообщениях электронной почты, загруженных из файла. В приведенном ниже примере кода показано, как это сделать:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "New display name 1"
msg.attachments[1].display_name = "New display name 2"
```