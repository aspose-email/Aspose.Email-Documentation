---
title: "Загрузка и сохранение сообщения"
url: /ru/python-net/loading-and-saving-message/
weight: 30
type: docs
---


## **Определение форматов файлов**
Aspose.Email API предоставляет возможность определять формат предоставленного файла сообщения. Для этого можно использовать метод DetectFileFormat класса FileFormatUtil. Для определения формата загруженного файла можно использовать следующие классы и методы.

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Class [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Class [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Метод detect_file_format (поток)
- Метод detect_file_format (путь_файла)

В следующем фрагменте кода показано, как определять форматы файлов.

```py
from aspose.email.tools import FileFormatUtil

# Detect file format and get the detected load format
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("The message format is: " + str(info.file_format_type))
```
## **Загрузка сообщения с опциями загрузки**
В следующем фрагменте кода показано, как загрузить сообщение с опциями загрузки.

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
### **Сохранение формата встроенного сообщения во время загрузки**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Embedded message file format: " + str(file_format))
```
## **Сохранение и преобразование сообщений**
Aspose.Email позволяет легко конвертировать сообщения любого типа в другой формат. Чтобы продемонстрировать эту функцию, приведенный в этой статье код загружает три типа сообщений с диска и сохраняет их в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) может использоваться для сохранения сообщений в других форматах. В статье показано, как использовать эти классы для сохранения образца электронного письма в виде:

- Формат EML.
- MSG для Outlook.
- Формат MHTML.
- Формат HTML.
### **Загрузка EML и сохранение как EML**
В следующем фрагменте кода показано, как загрузить сообщение EML и сохранить его на диск в том же формате.

```py
from aspose.email import MailMessage, SaveOptions

# Initialize and Load an existing EML file by specifying the MessageFormat
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```
### **Загрузка EML и сохранение как EML с сохранением исходных границ**
В следующем фрагменте кода показано, как загрузить EML и сохранить его как EML с сохранением исходных границ.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved original boundaries
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```
### **Сохранение в формате EML Сохранение вложений TNEF**
В следующем фрагменте кода показано, как сохранить вложения TNEF в формате EML.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved attachment
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```
### **Загрузка EML, сохранение в MSG**
В следующем фрагменте кода показано, как загрузить сообщение EML и преобразовать его в MSG, используя соответствующую опцию из [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save the Email message to disk in ASCII format and Unicode format
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```
### **Сохранение в формате MSG с сохраненными датами**
The [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) класс позволяет сохранить исходное сообщение в виде файла сообщений Outlook (MSG) с сохранением дат. В следующем фрагменте кода показано, как сохранить файл в формате MSG с сохраненными датами.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save as msg with preserved dates
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```
### **Сохранение почтового сообщения в формате MHTML**
Для получения желаемых результатов можно использовать различные варианты MHTML. В следующем фрагменте кода показано, как загрузить сообщение EML в[MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) и преобразует его в MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```
#### **Преобразование в MHTML с дополнительными настройками**

The [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) класс предоставляет дополнительные возможности для сохранения сообщений электронной почты в формате MHTML. Счетчик [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию по электронной почте в выходной файл MHTML. Можно записать следующие дополнительные поля:

 - НЕТ — конкретные настройки не указаны.
 - WRITE_HEADER — указывает, что необходимо записать информацию в заголовок.
 - WRITE_OUTLINE_ATTACHMENTS — указывает, что вложения с контурами должны быть записаны.
 - WRITE_COMPLETE_EMAIL_ADDRESS — указывает, что полный адрес электронной почты должен быть указан во всех заголовках письма.
 - NO_ENCODE_CHARACTERS — указывает, что не следует использовать передаточную кодировку символов.
 - HIDE_EXTRA_PRINT_HEADER — указывает, что заголовок страницы будет невидимым.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS — указывает, что полный адрес электронной почты должен быть указан в заголовке «Кому».
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS — указывает, что полный адрес электронной почты должен быть указан в заголовке «От».
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS — указывает, что полный адрес электронной почты должен быть записан в заголовке «Cc».
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS — указывает, что полный адрес электронной почты должен быть записан в заголовке «Bcc».
 - RENDER_CALENDAR_EVENT — указывает, что текст календарного события должен быть записан в выходной файл mhtml.
 - SKIP_BYTE_ORDER_MARK_IN_BODY — указывает, что байты с меткой порядка байтов (BOM) должны быть записаны в тело.
 - RENDER_V_CARD_INFO — указывает, что текст из vCard AlternativeView должен быть записан в выходной файл mhtml.
 - DISPLAY_AS_OUTLOOK — указывает, что заголовок From будет отображаться так же, как в Outlook.
 - RENDER_TASK_FIELDS — указывает, что конкретные поля задачи должны быть записаны в выходной файл mhtml.

В следующем фрагменте кода показано, как преобразовать файл eml в MHTML с дополнительными настройками.

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
#### **Отображение событий календаря при конвертации в MHTML**
The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) отображает события календаря в выходной файл MTHML.
В следующем фрагменте кода показано, как отображать события календаря при преобразовании в формат MHTML.

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
#### **Экспорт электронной почты в MHT без встроенных изображений**

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
#### **Экспорт электронной почты в MHT с настраиваемым часовым поясом**
[MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) класс предоставляет свойство TimeZoneOffset для установки настраиваемого часового пояса при экспорте в MHT. В следующем фрагменте кода показано, как экспортировать электронное письмо в MHT с помощью настраиваемого TimeZone.

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
### **Экспорт электронной почты в EML**
В следующем фрагменте кода показано, как экспортировать электронную почту в eml.

```py
from aspose.email import MailMessage, SaveOptions

# Load the EML file
msg = MailMessage.load(data_dir + "message.eml")

# Save the Email message as EML
msg.save(data_dir + "ExporttoEml_out.eml", SaveOptions.default_eml)
```
### **Сохранение сообщения в формате HTML**
The [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) класс позволяет экспортировать тело сообщения в HTML с возможностью экономии встроенных ресурсов. В следующем фрагменте кода показано, как сохранить сообщение в формате HTML, где значение embed_resources по умолчанию равно true.

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

### **Сохранение сообщения в виде файла шаблона Outlook (.oft)**
В следующем фрагменте кода показано, как сохранить сообщение в виде файла шаблона Outlook (.oft).

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "template subject", "Template body")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```
