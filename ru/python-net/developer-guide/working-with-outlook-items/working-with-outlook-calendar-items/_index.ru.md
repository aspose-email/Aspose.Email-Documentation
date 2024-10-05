---
title: "Работа с элементами календаря Outlook"
url: /ru/python-net/working-with-outlook-calendar-items/
weight: 80
type: docs
---


## **Работа с MapiCalendar**
Класс MapiCalendar библиотеки Aspose.Email предоставляет методы и атрибуты для установки различных свойств элемента календаря.

### **Создание и сохранение элементов календаря**
Следующий фрагмент кода показывает, как создать и сохранить элемент календаря в формате ICS.

```cs
import aspose.email as ae
from datetime import datetime

data_dir = "path/to/data/directory"

# Создание встречи
calendar = ae.mapi.MapiCalendar(
    "LAKE ARGYLE WA 6743",
    "Appointment",
    "Это очень важная встреча :)",
    datetime(2012, 4, 1),
    datetime(2012, 5, 1))

calendar.save(data_dir + "CalendarItem_out.ics", ae.calendar.AppointmentSaveFormat.ICS)
```
### **Сохранение элемента календаря в формате MSG**
Следующий фрагмент кода показывает, как сохранить элемент календаря в формате MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Установка идентификатора продукта при сохранении MapiCalendar в ICS**

Библиотека Aspose.Email позволяет сохранять MapiCalendar (элемент календаря) в файл ICS (iCalendar) с определёнными параметрами. С помощью свойств *ics_save_options.keep_original_date_time_stamp* и *ics_save_options.product_identifier* вы можете сохранить оригинальные временные метки, связанные с элементом календаря, и установить идентификатор продукта в файле ICS, например, "Foo Ltd". Идентификатор продукта — это поле, которое идентифицирует программное обеспечение или сервис, который сгенерировал файл ICS.

Вот пример кода, который позволяет установить идентификатор продукта при сохранении MapiCalendar в ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Получение общего числа событий**

Функция класса [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) позволяет читать данные календаря из указанного файла. Создавая объект CalendarReader, мы можем извлечь важную информацию, такую как общее количество событий, версия календаря, используемый метод и содержит ли календарь несколько событий. Следующий фрагмент кода демонстрирует, как работать с данными календаря и, дополнительно, загрузить встречи из календаря в виде списка нескольких событий.

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"Календарь содержит {reader.count} событий")
print(f"Версия календаря: {reader.version}")
print(f"Метод календаря: {reader.method}")
print(f"Содержит ли календарь несколько событий? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Добавление напоминания на экран в календарь**
Следующий фрагмент кода показывает, как добавить напоминание на экран в календарь.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Добавление аудио напоминания в календарь**
Следующий фрагмент кода показывает, как добавить аудио напоминание в календарь.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Добавление/извлечение вложений из файлов календаря**

Модуль Aspose.Email Calendar ("ae.calendar") также предоставляет функциональность для добавления и извлечения информации о вложениях.

- Чтобы включить вложение в встречу, создается объект "Attachment", указывая путь к файлу. Это вложение затем добавляется в список вложений встречи. Встреча сохраняется в определенном пути файла в формате iCalendar с помощью метода [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) и соответствующего формата файла.

- Чтобы извлечь вложения из встречи, её сначала загружают из сохраненного файла с помощью метода [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods), отображают количество вложений в "appointment2", а затем, итерируя по вложениям, выводят их имена.

Ниже приведен фрагмент кода, который демонстрирует, как создать встречи с вложениями, сохранить их и извлечь информацию о вложениях, используя модуль "ae.calendar". Он подчеркивает функциональность и возможности работы с встречами и вложениями в приложении календаря.

```python
import aspose.email as ae
import datetime as dt

# Добавление вложения в встречу
attendees = ae.MailAddressCollection()
attendees.append(ae.MailAddress("attendee@domain.com", "Получатель 1"))

appointment = ae.calendar.Appointment("Комната 112", dt.datetime(2023, 5, 27), dt.date(2023, 5, 28),  ae.MailAddress("organizer@domain.com"), attendees)

attachment = ae.Attachment("D:\\Aspose\\Files\\Attachment.txt")
appointment.attachments.append(attachment)

appointment.save("D:\\Aspose\\Files\\appWithAttachments_out.ics", ae.calendar.AppointmentSaveFormat.ICS)

# Извлечение вложений из встречи 
appointment2 = ae.calendar.Appointment.load("D:\\Aspose\\Files\\appWithAttachments_out.ics")
print(appointment2.attachments.length)
for att in appointment2.attachments:
    print(att.name)
```
### **Статус получателей из запроса на встречу**
Следующий фрагмент кода показывает, как получить статус получателей из запроса на встречу.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Конвертация EML-встречи в MSG с сохранением содержимого в формате HTML**

Aspose.Email позволяет конвертировать EML-встречу в MSG и сохранить HTML-содержимое. Свойство "forced_rtf_body_for_appointment" класса [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) используется для изменения типа содержимого встречи. При установке в *True* содержимое по умолчанию конвертируется в формат RTF. Чтобы сохранить содержимое в формате HTML, его следует установить в *False*. Следующий пример кода показывает, как сохранить HTML-содержимое встречи при конвертации из EML в MSG:

```python
import aspose.email as ae

eml = ae.MailMessage.load("appointment.eml")

conversionOptions = ae.mapi.MapiConversionOptions()
conversionOptions.format = ae.mapi.OutlookMessageFormat.UNICODE
# значение по умолчанию для ForcedRtfBodyForAppointment — true
conversionOptions.forced_rtf_body_for_appointment = False

msg = ae.mapi.MapiMessage.from_mail_message(eml, conversionOptions)

print(f"Тип содержимого: {msg.body_type}")

msg.save("appointment.msg")
```