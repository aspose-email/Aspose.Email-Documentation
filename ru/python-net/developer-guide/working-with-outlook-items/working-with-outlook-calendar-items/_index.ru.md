---
title: "Работа с элементами календаря Outlook"
url: /ru/python-net/working-with-outlook-calendar-items/
weight: 80
type: docs
---


## **Работа с MapiCalendar**
Класс MapicaLendar в Aspose.Email предоставляет методы и атрибуты для установки различных свойств элемента календаря.

### **Создание и сохранение элементов календаря**
В следующем фрагменте кода показано, как создать и сохранить элемент календаря в формате ICS.

```cs
import aspose.email as ae
from datetime import datetime

data_dir = "path/to/data/directory"

# Create the appointment
calendar = ae.mapi.MapiCalendar(
    "LAKE ARGYLE WA 6743",
    "Appointment",
    "This is a very important meeting :)",
    datetime(2012, 4, 1),
    datetime(2012, 5, 1))

calendar.save(data_dir + "CalendarItem_out.ics", ae.calendar.AppointmentSaveFormat.ICS)
```
### **Сохранение элемента календаря в формате MSG**
В следующем фрагменте кода показано, как сохранить элемент календаря в формате MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Настройка идентификатора продукта при сохранении MapicaLendar в ICS**

Библиотека Aspose.Email позволяет сохранить MapicaLendar (элемент календаря) в файл ICS (iCalendar) с определенными опциями. С помощью *ics_save_options.keep_original_date_time_stamp* and *ics_save_options.product_identifier* свойства: вы можете сохранить исходные метки даты и времени, связанные с элементом календаря, и задать идентификатор продукта в файле ICS, например «Foo Ltd», соответственно. Идентификатор продукта — это поле, в котором указано программное обеспечение или сервис, создавшие файл ICS.

Вот пример кода, который позволяет установить идентификатор продукта при сохранении MapicaLendar в ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Получение общего количества событий**

Функциональность [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) класс позволяет читать данные календаря из указанного файла. Создав объект CalendarReader, мы можем извлечь важную информацию, такую как общее количество событий, версия календаря, используемый метод и наличие в календаре нескольких событий. В следующем фрагменте кода показано, как работать с данными календаря и, кроме того, загружать встречи из календаря в виде списка нескольких событий.

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"Calendar contains {reader.count} events")
print(f"The Version of the calendar is {reader.version}")
print(f"The Method of the calendar is {reader.method}")
print(f"Is calendar contains contains multiple events? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Добавление экранного напоминания в календарь**
В следующем фрагменте кода показано, как добавить напоминание о отображении в календарь.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Добавление звукового напоминания в календарь**
В следующем фрагменте кода показано, как добавить звуковое напоминание в календарь.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Добавление/извлечение вложений из файлов календаря**

Модуль Aspose.Email Calendar («ae.calendar») также предоставляет возможность добавлять и извлекать информацию о вложениях.

- Чтобы добавить вложение к встрече, создается объект «Вложение» с указанием пути к файлу. Затем это вложение добавляется в список вложений к встрече. Встреча сохраняется в определенном пути к файлу в формате iCalendar с помощью [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) метод и соответствующий формат файла.

- Чтобы получить вложения о встрече, сначала они загружаются из сохраненного файла с помощью [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) Метод, при котором отображается количество вложений, присутствующих в «appointment2», и при повторном просмотре вложений печатаются их имена.

В приведенном ниже фрагменте кода показано, как создавать встречи с вложениями, сохранять их и извлекать информацию о вложениях с помощью модуля «ae.calendar». В нем описаны функциональные возможности и возможности работы с встречами и вложениями в приложение-календаре.

```python
import aspose.email as ae
import datetime as dt

# Add an attachment to an appointment
attendees = ae.MailAddressCollection()
attendees.append(ae.MailAddress("attendee@domain.com", "Recipient 1"))

appointment = ae.calendar.Appointment("Room 112", dt.datetime(2023, 5, 27), dt.date(2023, 5, 28),  ae.MailAddress("organizer@domain.com"), attendees)

attachment = ae.Attachment("D:\\Aspose\\Files\\Attachment.txt")
appointment.attachments.append(attachment)

appointment.save("D:\\Aspose\\Files\\appWithAttachments_out.ics", ae.calendar.AppointmentSaveFormat.ICS)

# Retrieve attachments from an appointment
appointment2 = ae.calendar.Appointment.load("D:\\Aspose\\Files\\appWithAttachments_out.ics")
print(appointment2.attachments.length)
for att in appointment2.attachments:
    print(att.name)
```
### **Статус получателей приглашения на собрание**
В следующем фрагменте кода показано, как определить статус получателей приглашения на собрание.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Преобразуйте EML Appointment в MSG с сохранением тела в формате HTML**

Aspose.Email позволяет преобразовывать встречи в формате EML в MSG и сохранять текст HTML. Свойство «forced_rtf_body_for_appointment» [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) класс используется для управления типом тела встречи. Если установлено значение *True*, тело по умолчанию преобразуется в формат RTF. Чтобы сохранить текст в формате HTML, его следует задать значение *False*. В следующем примере кода показано, как сохранить текст встречи в формате HTML при ее преобразовании из EML в MSG:

```python
import aspose.email as ae

eml = ae.MailMessage.load("appointment.eml")

conversionOptions = ae.mapi.MapiConversionOptions()
conversionOptions.format = ae.mapi.OutlookMessageFormat.UNICODE
# default value for ForcedRtfBodyForAppointment is true
conversionOptions.forced_rtf_body_for_appointment = False

msg = ae.mapi.MapiMessage.from_mail_message(eml, conversionOptions)

print(f"Body Type: {msg.body_type}")

msg.save("appointment.msg")
```