---
title: "Загрузка и Сохранение Сообщения"
url: /ru/python-net/loading-and-saving-message/
weight: 30
type: docs
---

## **Определение Форматов Файлов**
Aspose.Email API предоставляет возможность определять формат файла предоставленного сообщения. Метод DetectFileFormat класса FileFormatUtil может быть использован для достижения этой задачи. Следующие классы и методы могут быть использованы для определения загруженного формата файла.

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Class [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Class [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Метод detect_file_format(stream)
- Метод detect_file_format(file_path)

Следующий фрагмент кода показывает, как определить форматы файлов.

```py
from aspose.email.tools import FileFormatUtil

# Определить формат файла и получить определенный загружаемый формат
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("Формат сообщения: " + str(info.file_format_type))
```
## **Загрузка Сообщения с Параметрами Загрузки**
Следующий фрагмент кода показывает, как загрузить сообщение с параметрами загрузки.

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions

# Загрузить файлы Eml, html, mhtml, msg и dat
mail_message = MailMessage.load(data_dir + "message.eml", EmlLoadOptions())
MailMessage.load(data_dir + "description.html", HtmlLoadOptions())
MailMessage.load(data_dir + "message.mhtml", MhtmlLoadOptions())
MailMessage.load(data_dir + "message.msg", MsgLoadOptions())

# Загрузка с индивидуальными параметрами
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
### **Сохранение Вложенного Формата Сообщения при Загрузке**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Формат вложенного сообщения: " + str(file_format))
```
## **Сохранение и Конвертация Сообщений**
Aspose.Email облегчает конвертацию любого типа сообщения в другой формат. Чтобы продемонстрировать эту функцию, код в этой статье загружает три типа сообщений с диска и сохраняет их в других форматах. Базовый класс [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) и классы [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) могут быть использованы для дополнительных настроек при сохранении [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) в другие форматы. В статье показано, как использовать эти классы для сохранения примерного электронного письма в:

- EML формат.
- Outlook MSG.
- MHTML формат.
- HTML формат.
### **Загрузка EML и Сохранение как EML**
Следующий фрагмент кода показывает, как загрузить сообщение EML и сохранить его на диск в том же формате.

```py
from aspose.email import MailMessage, SaveOptions

# Инициализация и загрузка существующего файла EML, указав формат сообщения
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```
### **Загрузка EML и Сохранение как EML с Сохранением Исходных Границ**
Следующий фрагмент кода показывает, как загрузить EML и сохранить как EML, сохраняя исходные границы.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Сохранение как eml с сохранением оригинальных границ
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```
### **Сохранение как EML с Сохранением TNEF Вложений**
Следующий фрагмент кода показывает, как сохранить как EML, сохраняя TNEF вложения.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Сохранение как eml с сохранением вложения
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```
### **Загрузка EML, Сохранение в MSG**
Следующий фрагмент кода показывает, как загрузить сообщение EML и конвертировать его в MSG с использованием соответствующей опции из [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Инициализация и загрузка существующего файла EML, указав формат сообщения
eml = MailMessage.load(data_dir + "message.eml")

# Сохранение электронного письма на диск в ASCII и Unicode формате
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```
### **Сохранение как MSG с Сохранением Дат**
Класс [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) позволяет сохранять исходное сообщение в виде файла Outlook Message (MSG), сохраняя даты. Следующий фрагмент кода показывает, как сохранить как MSG с сохранением дат.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Инициализация и загрузка существующего файла EML, указав формат сообщения
eml = MailMessage.load(data_dir + "message.eml")

# Сохранение как msg с сохранением дат
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```
### **Сохранение MailMessage как MHTML**
Различные параметры MHTML могут быть использованы для достижения желаемых результатов. Следующий фрагмент кода показывает, как загрузить сообщение EML в [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) и конвертировать его в MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Инициализация и загрузка существующего файла EML, указав формат сообщения
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```
#### **Конвертация в MHTML с Дополнительными Настройками**

Класс [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) предоставляет дополнительные параметры для сохранения сообщений электронной почты в формате MHTML. Перечисление [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) позволяет записывать дополнительную информацию о сообщении в выходное MHTML. Следующие дополнительные поля могут быть записаны:

 - NONE - Не указаны специфические настройки.
 - WRITE_HEADER - Указывает, что информация заголовка должна быть записана.
 - WRITE_OUTLINE_ATTACHMENTS - Указывает, что вложенные файлы должны быть записаны.
 - WRITE_COMPLETE_EMAIL_ADDRESS - Указывает, что полный адрес электронной почты должен быть записан во всех заголовках электронной почты.
 - NO_ENCODE_CHARACTERS - Указывает, что не должна использоваться передача кодирования символов.
 - HIDE_EXTRA_PRINT_HEADER - Указывает, что заголовок страницы будет невидимым.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS - Указывает, что полный адрес электронной почты должен быть записан в заголовке "To".
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS - Указывает, что полный адрес электронной почты должен быть записан в заголовке "From".
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS - Указывает, что полный адрес электронной почты должен быть записан в заголовке "Cc".
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS - Указывает, что полный адрес электронной почты должен быть записан в заголовке "Bcc".
 - RENDER_CALENDAR_EVENT - Указывает, что текст календарного события должен быть записан в выходное MHTML.
 - SKIP_BYTE_ORDER_MARK_IN_BODY - Указывает, что байты метки порядка байтов (BOM) должны быть записаны в тело.
 - RENDER_V_CARD_INFO - Указывает, что текст из VCard AlternativeView должен быть записан в выходное MHTML.
 - DISPLAY_AS_OUTLOOK - Указывает, что заголовок "From" будет отображаться как в Outlook.
 - RENDER_TASK_FIELDS - Указывает, что конкретные поля задач должны быть записаны в выходное MHTML.

Следующий фрагмент кода показывает, как конвертировать файл eml в MHTML с дополнительными настройками.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MailMessageSaveType, FileCompatibilityMode

# Загрузка существующего файла EML
eml = MailMessage.load(data_dir + "message.eml")

# Сохранение как mht с заголовком
mht_save_options = MhtSaveOptions()

# Укажите требуемые параметры форматирования
# Здесь мы указываем записать информацию заголовка в выходной файл без записи дополнительного печатного заголовка
# и выходные заголовки должны отображаться как оригинальные заголовки в сообщении
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.HIDE_EXTRA_PRINT_HEADER | MhtFormatOptions.DISPLAY_AS_OUTLOOK

# Проверьте кодировку содержимого тела на корректность.
mht_save_options.check_body_content_encoding = True

eml.save(data_dir + "outMessage_out.mht", mht_save_options)
```
#### **Отображение Календарных Событий при Конвертации в MHTML**
Параметр [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) выводит календарные события в выходное MTHML.
Следующий фрагмент кода показывает, как отображать календарные события при конвертации в MHTML.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

file_name = "message.msg"

# Загрузка файла MSG
msg = MailMessage.load(data_dir + file_name)

# Создание параметров сохранения MHT
options = MhtSaveOptions()
options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.RENDER_CALENDAR_EVENT

# Сохранение сообщения как MHTML
msg.save(data_dir + "Meeting with Recurring Occurrences.mhtml", options)
```
#### **Экспорт Электронной Почты в MHT без Встраиваемых Изображений**

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

# Загрузка файла EML
eml = MailMessage.load(data_dir + "message.eml")

# Создание параметров сохранения MHT
mht_save_options = MhtSaveOptions()
mht_save_options.skip_inline_images = True

# Сохранение сообщения как MHTML без встроенных изображений
eml.save(data_dir + "EmlToMhtmlWithoutInlineImages_out.mht", mht_save_options)
```
#### **Экспорт Электронной Почты в MHT с Пользовательским Часовым Поясом**
Класс [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) предоставляет свойство TimeZoneOffset для установки пользовательского часового пояса при экспорте в MHT. Следующий фрагмент кода показывает, как экспортировать электронное письмо в MHT с пользовательским часовым поясом.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode
from datetime import timedelta

# Загрузка файла EML
eml = MailMessage.load(data_dir + "message.eml")

# Установите местное время для даты сообщения
eml.time_zone_offset = timedelta(hours=-8)

# Даты будут отображены по часовому поясу местной системы
mht_save_options = MhtSaveOptions()
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER
eml.save(data_dir + "ExportEmailToMHTWithCustomTimezone_out.mhtml", mht_save_options)
```
### **Экспорт Электронной Почты в EML**
Следующий фрагмент кода показывает, как экспортировать электронное письмо в eml.

```py
from aspose.email import MailMessage, SaveOptions

# Загрузка файла EML
msg = MailMessage.load(data_dir + "message.eml")

# Сохранить электронное сообщение как EML
msg.save(data_dir + "ExporttoEml_out.eml", SaveOptions.default_eml)
```
### **Сохранение Сообщения как HTML**
Класс [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) позволяет экспортировать тело сообщения в HTML с параметром для сохранения встроенных ресурсов. Следующий фрагмент кода показывает, как сохранить сообщение как HTML, где значение по умолчанию для embed_resources равно true.

```py
from aspose.email import MailMessage, SaveOptions, HtmlSaveOptions, HtmlFormatOptions

# Загрузка файла EML
message = MailMessage.load(data_dir + "message.eml")

# Сохранение электронного сообщения как HTML
message.save(data_dir + "SaveAsHTML_out.html", SaveOptions.default_html)

# ИЛИ

eml = MailMessage.load(data_dir + "message.eml")
options = HtmlSaveOptions()
options.embed_resources = False
options.html_format_options = (
    HtmlFormatOptions.WRITE_HEADER
    | HtmlFormatOptions.WRITE_COMPLETE_EMAIL_ADDRESS
)  # сохранить заголовки сообщения в выходном HTML, используя параметры форматирования
eml.save(data_dir + "SaveAsHTML1_out.html", options)
```

### **Сохранение Сообщения как Шаблон Outlook (.oft)**
Следующий фрагмент кода показывает, как сохранить сообщение как шаблон Outlook (.oft) файл.

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "тема шаблона", "Тело шаблона")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```