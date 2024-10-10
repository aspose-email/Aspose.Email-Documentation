---
title: "Управление файлами сообщений с помощью Aspose.Email.Outlook"
url: /ru/python-net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Определение типа элемента MAPI в папке PST**

Файл PST обычно содержит различные типы данных, такие как электронные письма, события календаря, контакты и многое другое. Класс [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) библиотеки Aspose.Email позволяет вам получать доступ и классифицировать различные типы элементов MAPI в файле PST. Приведенный ниже код демонстрирует, как определить тип элемента MAPI в папке PST:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Получить тип класса на основе msg.SupportedType
    item_type = msg.supported_type

    # Не поддерживаемый тип. Доступ как соответствующий элемент недоступен.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Тип элемента не поддерживается")
    # Электронное сообщение.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # Вы можете получить доступ к свойствам MapiMessage там.
        # Например, тема
        print(msg.subject)
    # Элемент контакта. Доступ как MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiContact там. 
        # Например, name_info.display_name. 
        print(contact.name_info.display_name)
    # Элемент календаря. Доступ как MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiCalendar там. 
        # Например, местоположение. 
        print(calendar.location)
    # Рассылка. Доступ как MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiDistributionList там
    # Запись журнала. Доступ как MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiJournal там
    # StickyNote. Доступ как MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiNote там
    # Элемент задачи. Доступ как MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # Вы можете получить доступ к свойствам MapiTask там

```

## **Конвертирование MSG в MIME сообщение**
API Aspose.Email предоставляет возможность конвертации файла MSG в MIME сообщение с помощью метода ToMailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Установка времени ожидания для конвертации и загрузки сообщения**

Чтобы ограничить время в миллисекундах для конвертации сообщения (значение по умолчанию 3 сек), используется свойство **timeout** класса [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class). 

Вот как вы можете установить время ожидания для процессов конвертации и загрузки сообщения:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

Установив время ожидания для процессов конвертации и загрузки сообщения, вы можете контролировать максимальное время, в течение которого эти операции могут выполняться. После установки времени ожидания вы можете продолжить с процессами конвертации и загрузки вашего сообщения. 


## **Обработка файлов шаблонов Outlook (OFT)** 

### **Загрузка, изменение и сохранение файла OFT**

Шаблоны Outlook (OFT) обеспечивают удобный способ оптимизации процесса отправки повторяющихся электронных сообщений. Вместо того чтобы каждый раз создавать одно и то же электронное письмо с нуля, вы можете создать сообщение в Outlook и сохранить его как шаблон Outlook (OFT). Позже, когда вам нужно будет отправить аналогичное сообщение, вы можете быстро сгенерировать его из шаблона. Этот подход экономит вам усилия по переписыванию одного и того же контента в теле сообщения, указания темы письма, форматирования и многого другого.

Класс [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) библиотеки Aspose.Email обеспечивает мощный инструмент для загрузки и изменения файлов шаблонов Outlook (OFT). Как только шаблон Outlook загружен в экземпляр класса MailMessage, вы можете легко обновить такие свойства, как отправитель, получатель, текст сообщения, тема и различные другие атрибуты.

```py
import aspose.email as ae

# Загрузка файла OFT
oft_file_path = "your_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Обновите свойства по мере необходимости
mail_message.subject = "Обновленная тема"
mail_message.body = "Обновленный текст сообщения."

# Сохраните обновленное сообщение как файл MSG
msg_file_path = "updated_message.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Обновленное сообщение сохранено в {msg_file_path}")
```
После внесения необходимых изменений вы можете отправить электронное письмо, используя класс [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class):

```py
# Отправить электронное письмо
smtpClient.send(message)
```

### **Сохранение файла Outlook MSG как шаблона**

Для этой цели вы можете использовать класс [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) для создания электронного письма, а затем сохранить его как файл OFT. Пример кода ниже покажет, как сохранить электронное письмо как шаблон Outlook:

```py
import aspose.email as ae

# Создание нового MailMessage
message = ae.MailMessage()
message.subject = "Шаблон Outlook"
message.html_body = "<html><body>Это текст тела электронной почты.</body></html>"
message.from_address = ae.MailAddress("your.email@example.com", "Ваше Имя")

# Сохраните MailMessage как файл шаблона Outlook (OFT)
oft_file_path = "sample_template.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Шаблон Outlook сохранен как {oft_file_path}")
```
### **OFT или MSG: Определение типа MapiMessage**

Следующий фрагмент кода иллюстрирует, как определить, представляет ли загруженное сообщение MAPI стандартное электронное сообщение или шаблон Outlook (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # возвращает false

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # возвращает true
```
После загрузки файла MSG код проверяет, является ли свойство **is_template** класса [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) истинным или ложным. В случае, если оно возвращает *false*, загруженное сообщение является стандартным электронным сообщением, а не шаблоном Outlook; в противном случае, если оно возвращает *true*, сообщение не является стандартным электронным сообщением, это шаблон Outlook.

### **Сохранение MapiMessage или MailMessage в формате OFT** 

[SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) - это абстрактный базовый класс для классов, которые позволяют пользователю указывать дополнительные параметры при сохранении MailMessage в определенном формате. Пример кода ниже демонстрирует, как сохранить сообщение в формате OFT:

```py
import aspose.email as ae

# Сохранение MailMessage в формате OFT
eml = ae.MailMessage.load("message.eml")

eml.save("message.oft", ae.SaveOptions.default_oft)

# или альтернативный способ 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# или альтернативный способ 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# Сохранение MapiMessage в формате OFT
msg = ae.mapi.MapiMessage.load("message.msg")

msg.save("message.oft", ae.SaveOptions.default_oft)

# или альтернативный способ 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)

# или альтернативный способ 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)
```

## **Управление сообщениями с цифровыми подписями**

Библиотека предоставляет класс [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class), абстрактный базовый класс для классов, которые позволяют пользователю указывать дополнительные параметры при загрузке MailMessage из определенного формата. Опция сохранения подписи устанавливается по умолчанию.

### **Конвертация из EML в MSG с сохранением подписи** 

Пример кода ниже демонстрирует, как загрузить сообщение, конвертировать его в формат MSG и сохранить как MSG (подпись сохраняется по умолчанию): 

```python

import aspose.email as ae

# Загрузка почтового сообщения
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Сохранить как MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

### **Конвертация S/MIME сообщений из MSG в EML**

Aspose.Email позволяет конвертировать из MSG в EML с сохранением цифровой подписи, как показано в следующем фрагменте кода.

```python
import aspose.email as ae

# Загрузка почтового сообщения
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Сохранить файл на диск
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
## **Установка цветовой категории для файлов Outlook MSG**

Иногда вам может понадобиться различать электронные письма определенной важности и визуально организовывать их. Библиотека предоставляет способ сделать это, присваивая сообщение определенный цвет. Когда вы устанавливаете цветовую категорию для элемента, это позволяет вам легко идентифицировать и находить связанные элементы одним взглядом. Используйте класс [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class), чтобы установить цветовую категорию для сообщения, как в следующем примере кода:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Добавить две категории
ae.mapi.FollowUpManager.add_category(msg, "Фиолетовая категория")
ae.mapi.FollowUpManager.add_category(msg, "Красная категория")

# Получить список доступных категорий
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Удалить указанную категорию, а затем очистить все категории
ae.mapi.FollowUpManager.remove_category(msg, "Красная категория")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Доступ к информации о последующих действиях из MSG файла**

### **Извлечение информации о счетах и подтверждениях доставки**

Пример кода ниже демонстрирует, как извлечь информацию о получателе и их статус отслеживания из сообщения Outlook (MSG):

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Получатель: {recipient.display_name}")
    print(f"Время доставки:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Время прочтения:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Создание пересылаемых и ответных сообщений**

Aspose.Email предоставляет простые способы создания пересылаемых и ответных сообщений на основе существующих.

### **Создание пересылаемого сообщения**

Вы можете использовать класс [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) для создания пересылаемого сообщения, задав исходное сообщение, отправителя, получателей, тему и текст. Пересылаемые сообщения могут включать оригинальное сообщение как вложение или как тело пересылаемого сообщения. У вас есть возможность настраивать дополнительные свойства, такие как вложения, заголовки и параметры форматирования. Пример кода ниже показывает, как создать пересылаемое сообщение:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")

```

### **Создание ответного сообщения**

Класс [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) используется для конфигурации настроек ответа, включая исходное сообщение, отправителя, получателей, режим ответа, префикс темы и текст ответа. Ответные сообщения могут быть созданы в различных режимах ответа, таких как "Ответить отправителю" или "Ответить всем" в зависимости от ваших требований. Вы можете настроить различные свойства, такие как вложения, заголовки и параметры форматирования для ответа. Пример кода ниже показывает, как создать ответное сообщение:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Установить свойства ReplyMessageBuilder
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Уважаемый друг,</b></p> Я хочу представить моего соавтора и соучителя. <p><a href=\"www.google.com\">Это первая ссылка</a></p><p><a href=\"www.google.com\">Это вторая ссылка</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")

```