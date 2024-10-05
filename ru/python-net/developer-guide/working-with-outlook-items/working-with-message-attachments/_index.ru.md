---
title: "Работа с вложениями сообщений"
url: /ru/python-net/working-with-message-attachments/
weight: 70
type: docs
---


## **Управление вложениями с помощью Aspose Outlook**
Создание и сохранение файлов сообщений Outlook (MSG) объясняет, как создавать и сохранять сообщения, а также как создавать MSG файлы с вложениями. В этой статье объясняется, как управлять вложениями Microsoft Outlook с помощью Aspose.Email. Вложения из файла сообщения доступны и сохраняются на диск с помощью свойства Attachments класса MapiMessage. Свойство Attachments представляет собой коллекцию типа MapiAttachmentCollection.

### **Проверка, является ли вложение встроенным или обычным**

"Встроенные" и "Обычные" вложения относятся к способу их включения в электронное сообщение. **Обычные** вложения — это файлы, прикрепленные традиционным способом. Обычно они отображаются в списке в почтовом клиенте и могут быть загружены получателем и сохранены на локальное хранилище. **Встроенные** вложения, также известные как встраиваемые или встроенные изображения, обычно используются для включения изображений или других медиа в текст сообщения. Они не отображаются в отдельном списке, но отображаются непосредственно в содержании электронной почты, например, в теле письма. Это позволяет включать изображения или другие медиа, которые являются частью содержимого сообщения. Пример кода ниже демонстрирует, как определить, является ли вложение встроенным или обычным:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Сохранение вложений из файла сообщения Outlook (MSG)**

Чтобы сохранить вложения из файла MSG:

1. Переберите коллекцию MapiAttachmentCollection и получите отдельные вложения.
1. Чтобы сохранить вложения, вызовите метод Save() класса MapiAttachment.

Следующий фрагмент кода показывает, как сохранить вложения на локальный диск.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Создайте экземпляр MapiMessage из файла
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Переберите коллекцию вложений
for attachment in message.attachments:
    # Сохраните отдельное вложение
    attachment.save(data_dir + attachment.file_name)
```

### **Получение вложений вложенных почтовых сообщений**

Встраиваемые OLE-вложения также появляются в коллекции Attachment класса MapiMessage. В следующем примере кода анализируется файл сообщения для встроенных вложений сообщений и сохраняется на диск. Статический метод FromProperties() класса MapiMessage может создать новое сообщение из встроенного вложения. Следующий фрагмент кода показывает, как получить вложенные почтовые сообщения.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Создайте объект MapiMessage из отдельного вложения
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Создайте объект типа MailMessageInterpreter из вышеуказанного сообщения и сохраните встроенное сообщение в файл на диске
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Удаление вложений**

Библиотека Aspose Outlook предоставляет функциональность для удаления вложений из файлов Microsoft Outlook Message (.msg):

- Вызовите метод RemoveAttachments(). Он принимает путь к файлу сообщения в качестве параметра. Реализован как публичный статический метод, поэтому вам не нужно создавать экземпляр объекта.

Следующий фрагмент кода показывает, как удалить вложения.

```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

Вы также можете вызвать статический метод класса MapiMessage DestroyAttachment(). Он работает быстрее, чем RemoveAttachment(), потому что метод RemoveAttachment() анализирует файл сообщения.

```py
import aspose.email as ae

# Удалите вложения в MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Добавление вложений MSG**

Сообщение Outlook может содержать другие сообщения Microsoft Outlook во вложениях как обычные или встроенные сообщения. Коллекция MapiAttachmentCollection предоставляет перегруженные методы метода Add для создания сообщений Outlook с обоими типами вложений.
{{% alert %}}
**Попробуйте!**

Добавляйте или удаляйте вложения электронной почты онлайн с бесплатным [**Aspose.Email Editor App**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление ссылочного вложения в MapiMessage**

"Ссылочное вложение" обычно относится к вложению, которое содержит ссылку или ссылку на внешний ресурс, а не на сам файл. Эти ссылки часто используются в HTML-эмейлах для ссылок на внешние изображения или ресурсы, размещенные на удаленном сервере. Вместо встраивания полного файла ссылочное вложение включает URL или ссылку на внешний контент.

Aspose.Email предоставляет набор инструментов для корректного отображения ссылочных вложений, представленное в следующем примере кода:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Добавьте ссылочное вложение
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# Вы также можете установить дополнительные свойства вложения
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Наконец, сохраните сообщение
msg.save("msg_with_ref_attach.msg")
```
### **Встраивание сообщения как вложения**
Следующий фрагмент кода показывает, как встроить файлы MSG в файл MSG, который содержит PR_ATTACH_METHOD со значением 5.

```py
import aspose.email as ae

# Создайте новый MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "Это тело сообщения")

# Загрузите сообщение-вложение
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Добавьте вложение к сообщению
message.attachments.add("Weekly report.msg", attach_msg)

# Сохраните сообщение с вложенным сообщением
message.save("WithEmbeddedMsg_out.msg")
```
### **Чтение встроенных сообщений из вложений**
Следующий фрагмент кода показывает, как читать встроенное сообщение из вложения.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Загрузите MapiMessage из файла
message = ae.mapi.MapiMessage.from_file(file_name)

# Проверьте, является ли первое вложение сообщением Outlook
if message.attachments[0].object_data.is_outlook_message:
    # Получите встроенное сообщение как MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Выполните дальнейшие действия с встроенным сообщением
    # ...
```
## **Вставка и замена вложений**
API Aspose.Email предоставляет возможность вставлять вложения в определенный индекс в родительском сообщении. Он также предоставляет возможность заменять содержимое вложения другим вложением сообщения. Следующий фрагмент кода показывает, как выполнять вставку и замену вложений.
### **Вставка в конкретное место**
API Aspose.Email предоставляет возможность вставки вложения MSG в родительский MSG с использованием метода Insert коллекции MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). Следующий фрагмент кода показывает, как выполнить вставку в определенном месте.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Загрузите MapiMessage из файла
message = ae.mapi.MapiMessage.load(file_name)

# Сохраните вложение в поток памяти
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Загрузите вложение из потока памяти
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Вставьте загруженное вложение по индексу 1
message.attachments.insert(1, "new 11", get_data)
```
### **Замена содержимого вложения**
Это можно использовать для замены содержимого встроенного вложения на новые с помощью метода Replace. Однако его нельзя использовать для вставки вложения с PR_ATTACH_NUM = 4 (например) в коллекцию с collection.Count = 2. Следующий фрагмент кода показывает, как заменить содержимое вложения.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Загрузите MapiMessage из файла
message = ae.mapi.MapiMessage.load(file_name)

# Сохраните вложение в поток памяти
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Загрузите вложение из потока памяти
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Замените вложение по индексу 1 на загруженное вложение
message.attachments.replace(1, "new 1", get_data)
```
### **Переименование вложения в MapiMessage**

Можно изменить отображаемые имена вложений в электронных сообщениях, загруженных из файла. Пример кода ниже показывает, как это сделать:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "Новое отображаемое имя 1"
msg.attachments[1].display_name = "Новое отображаемое имя 2"
```