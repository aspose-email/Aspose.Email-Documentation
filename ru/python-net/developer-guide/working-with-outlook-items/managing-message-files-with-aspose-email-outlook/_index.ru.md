---
title: "Управление файлами сообщений с помощью Aspose.Email.Outlook"
url: /ru/python-net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Определите тип элемента MAPI в папке PST**

Файл PST обычно содержит различные типы данных, такие как сообщения электронной почты, события календаря, контакты и многое другое. [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) класс Aspose.Email позволяет вам получать доступ к различным типам элементов MAPI и классифицировать их в файле PST. В приведенном ниже коде показано, как определить тип элемента MAPI в папке PST:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Get the class type based on msg.SupportedType
    item_type = msg.supported_type

    # Non-supported type. It cannot be accessed as appropriate item type.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Item type not supported")
    # An email message.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # You can access to MapiMessage properties there.
        # A subject for example
        print(msg.subject)
    # A contact item. Can be accessed as MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # You can access to MapiContact properties there.
        # A name_info.display_name for example.
        print(contact.name_info.display_name)
    # A calendar item. Can be accessed as MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # You can access to MapiCalendar properties there.
        # A location for example.
        print(calendar.location)
    # A distribution list. Can be accessed as MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # You can access to MapiDistributionList properties there
    # A Journal entry. Can be accessed as MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # You can access to MapiJournal properties there
    # A StickyNote. Can be accessed as MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # You can access to MapiNote properties there
    # A Task item. Can be accessed as MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # You can access to MapiTask properties there

```

## **Преобразование MSG в сообщение MIME**
Aspose.Email API предоставляет возможность преобразования файла MSG в сообщение MIME с помощью метода toMailMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Настройка тайм-аута для конвертации и загрузки сообщения**

Чтобы ограничить время преобразования сообщения в миллисекундах (значение по умолчанию 3 секунды), **timeout** собственность [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class) используется класс.

Вот как можно установить тайм-аут для процессов преобразования и загрузки сообщений:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

Установив тайм-аут для процессов преобразования и загрузки сообщений, вы можете контролировать максимальное время выполнения этих операций. После установки тайм-аута вы можете приступить к процессам преобразования и загрузки сообщений.


## **Обработка файлов шаблонов Outlook (OFT)**

### **Загрузка, изменение и сохранение файла OFT**

Шаблоны Outlook (OFT) предлагают удобный способ упростить процесс отправки повторяющихся сообщений электронной почты. Вместо того чтобы каждый раз составлять одно и то же письмо с нуля, можно создать сообщение в Outlook и сохранить его как шаблон Outlook (OFT). Позже, когда вам понадобится отправить аналогичное сообщение, вы сможете быстро сгенерировать его на основе шаблона. Такой подход избавляет вас от необходимости переписывать одно и то же содержимое в тексте сообщения, указывать тему, форматирование и многое другое.

Aspose.Email's [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) класс предоставляет мощный инструмент для загрузки и управления файлами шаблонов Outlook (OFT). После загрузки шаблона Outlook в экземпляр класса MailMessage можно легко обновить такие свойства, как отправитель, получатель, текст сообщения, тема и различные другие атрибуты.

```py
import aspose.email as ae

# Load the OFT file
oft_file_path = "your_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Update properties as needed
mail_message.subject = "Updated Subject"
mail_message.body = "Updated body text."

# Save the updated message as an MSG file
msg_file_path = "updated_message.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Updated message saved to {msg_file_path}")
```
После внесения необходимых обновлений вы можете отправить электронное письмо, используя [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

```py
# Send the email
smtpClient.send(message)
```

### **Сохранение MSG-файла Outlook в качестве шаблона**

Для этого вы можете использовать [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) класс для создания электронного письма, а затем его сохранения в виде файла OFT. В следующем примере кода показано, как сохранить электронное письмо в качестве шаблона Outlook:

```py
import aspose.email as ae

# Create a new MailMessage
message = ae.MailMessage()
message.subject = "Sample Outlook Template"
message.html_body = "<html><body>This is the body of the email.</body></html>"
message.from_address = ae.MailAddress("your.email@example.com", "Your Name")

# Save the MailMessage as an Outlook Template (OFT) file
oft_file_path = "sample_template.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Outlook Template saved as {oft_file_path}")
```
### **OFT или MSG: определите тип сообщения MapiMessage**

В следующем фрагменте кода показано, как определить, является ли загруженное сообщение MAPI стандартным сообщением электронной почты или шаблоном Outlook (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # returns false

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # returns true
```
После загрузки файла MSG код проверяет, **is_template** собственность [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) класс имеет значение True или False. В случае, если он вернется *false*, загруженное сообщение является стандартным сообщением электронной почты, а не шаблоном Outlook, в противном случае, если оно вернется *true*, сообщение не является стандартным сообщением электронной почты, а шаблоном Outlook.

### **Сохранение MAPIMessage или MailMessage в формате OFT**

The [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) это абстрактный базовый класс для классов, которые позволяют пользователю указывать дополнительные параметры при сохранении MailMessage в определенном формате. В следующем примере кода показано, как сохранить сообщение в формате OFT:

```py
import aspose.email as ae

# Save the MailMessage to OFT format
eml = ae.MailMessage.load("message.eml")

eml.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# Save the MapiMessage to OFT format
msg = ae.mapi.MapiMessage.load("message.msg")

msg.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)
```

## **Управление сообщениями с помощью цифровых подписей**

Библиотека предоставляет [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class) class, абстрактный базовый класс для классов, которые позволяют пользователю указывать дополнительные параметры при загрузке MailMessage из определенного формата. Опция сохранения подписи установлена по умолчанию.

### **Преобразование из EML в MSG с сохранением подписи**

В приведенном ниже примере кода показано, как загрузить сообщение, преобразовать его в формат MSG и сохранить как MSG (подпись по умолчанию сохраняется):

```python

import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Save as MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

### **Преобразование сообщений S/MIME из MSG в EML**

Aspose.Email позволяет конвертировать MSG в EML с сохранением цифровой подписи, как показано в следующем фрагменте кода.

```python
import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Save File to disk
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
## **Настройка цветовой категории для файлов Outlook MSG**

Иногда вам может понадобиться различать особо важные электронные письма и визуально упорядочить их. Библиотека позволяет сделать это, присвоив элементу сообщения определенный цвет. Когда вы задаете цветовую категорию для элемента, вы можете легко идентифицировать и находить похожие элементы с первого взгляда. Используйте [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) класс для установки цветовой категории сообщения, как показано в следующем примере кода:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Add Two categories
ae.mapi.FollowUpManager.add_category(msg, "Purple Category")
ae.mapi.FollowUpManager.add_category(msg, "Red Category")

# Retrieve the list of available categories
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Remove the specified category and then Clear all categories
ae.mapi.FollowUpManager.remove_category(msg, "Red Category")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Доступ к последующей информации из файла MSG**

### **Извлеките информацию о прочтении и получении**

В приведенном ниже примере кода показано, как извлечь информацию о получателях и их статус отслеживания из файла сообщений Outlook (MSG):

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Recipient: {recipient.display_name}")
    print(f"Delivery time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Read time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Создание сообщений для пересылки и ответа**

Aspose.Email предоставляет простые способы создания сообщений для пересылки и ответа на основе существующих.

### **Создание пересылающего сообщения**

Вы можете использовать [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) класс для создания пересылаемого сообщения путем установки исходного сообщения, отправителя, получателей, темы и текста. Пересылаемые сообщения могут содержать исходное сообщение в виде вложения или текста пересылаемого сообщения. У вас есть возможность настраивать дополнительные свойства, такие как вложения, заголовки и параметры форматирования. В приведенном ниже примере кода показано, как создать пересылаемое сообщение:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")

```

### **Создание ответного сообщения**

The [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) класс используется для настройки параметров ответа, включая исходное сообщение, отправителя, получателей, режим ответа, префикс темы и тело ответного сообщения. В зависимости от ваших требований ответные сообщения можно создавать в разных режимах ответа, таких как «Ответить отправителю» или «Ответить всем». Можно настроить различные свойства, такие как вложения, заголовки и параметры форматирования ответного сообщения. В приведенном ниже примере кода показано, как создать пересылаемое сообщение:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Set ReplyMessageBuilder Properties
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")

```
