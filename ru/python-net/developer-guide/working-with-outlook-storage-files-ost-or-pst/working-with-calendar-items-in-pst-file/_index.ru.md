---
title: "Работа с элементами календаря в файле PST"
url: /ru/python-net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Добавление MapiCalendar в PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapicaLendar в подпапку «Календарь» созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapicaLendar в PST:

1. Создайте объект MapicaLendar.
1. Задайте свойства MapicaLendar с помощью конструктора и методов.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предопределенную папку (Calendar) в корне файла PST, открыв корневую папку и вызвав метод add_mapi_message_item ().

В следующем фрагменте кода показано, как создать файл MapicaLendar, а затем добавить его в папку календаря вновь созданного файла PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Сохранение элементов календаря из PST на диск в формате ICS**
В этой статье показано, как получить доступ к элементам календаря из файла Outlook PST и сохранить календарь на диск в формате ICS. Используйте классы PersonalStorage и MapicaLendar для получения информации из календаря. Ниже приведены шаги по сохранению элементов календаря:

1. Загрузите файл PST в класс PersonalStorage.
1. Перейдите в папку «Календарь».
1. Получите содержимое папки «Календарь», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Вызовите метод PersonalStorage.extract_Message (), чтобы получить контактную информацию в классе MapicaLendar.
1. Вызовите метод MapiCalendar.save (), чтобы сохранить элемент календаря на диск в формате ICS.

Приведенная ниже программа загружает файл PST с диска и сохраняет все элементы календаря в формате ICS. Затем файлы ICS можно использовать в любой другой программе, которая может загрузить стандартный файл календаря ICS. Файл ICS, открытый в Microsoft Outlook, выглядит так, как показано на скриншоте ниже.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
|: - |
В следующем фрагменте кода показано, как экспортировать элементы календаря из Outlook PST в формат ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Сохранение в виде ICS с исходной меткой времени**

The *keep_original_date_time_stamp* метод [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) класс позволяет сохранить исходные метки даты и времени элементов календаря при их сохранении в виде файла ICS (iCalendar). Следующий пример кода демонстрирует реализацию этого метода:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

calendar_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.APPOINTMENTS)

for msg_info in calendar_folder.enumerate_messages():
    cal = pst.extract_message(msg_info).to_mapi_message_item()

    save_options = ae.mapi.MapiCalendarIcsSaveOptions()
    save_options.keep_original_date_time_stamp = True

    if not (cal is None):
      cal.save("cal.ics", save_options)
```
## **Изменить/удалить повторения из повторов**

Исключения можно добавлять к существующим рекурсиям с помощью Aspose.Email для .NET API. Следующий пример кода иллюстрирует использование этой функции. 

```py
from datetime import datetime, timedelta
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion
from aspose.email.mapi import MapiCalendar, MapiCalendarEventRecurrence, \
    MapiCalendarDailyRecurrencePattern, MapiCalendarRecurrenceEndType, \
    MapiCalendarExceptionInfo, MapiCalendarRecurrencePatternType, \
    MapiRecipientCollection, MapiRecipientType

start_date = datetime.now().date()

recurrence = MapiCalendarEventRecurrence()
pattern = MapiCalendarDailyRecurrencePattern()
pattern.pattern_type = MapiCalendarRecurrencePatternType.DAY
pattern.period = 1
pattern.end_type = MapiCalendarRecurrenceEndType.NEVER_END
recurrence.recurrence_pattern = pattern

exception_date = start_date + timedelta(days=1)

# adding one exception
exception_info = MapiCalendarExceptionInfo()
exception_info.location = "London"
exception_info.subject = "Subj"
exception_info.original_start_date = exception_date
exception_info.start_date_time = exception_date
exception_info.end_date_time = exception_date + timedelta(hours=5)
pattern.exceptions.append(exception_info)
pattern.modified_instance_dates.append(exception_date)
# every modified instance also has to have an entry in the DeletedInstanceDates field with the original instance date.
pattern.deleted_instance_dates.append(exception_date)

# adding one deleted instance
pattern.deleted_instance_dates.append(exception_date + timedelta(days=2))

rec_coll = MapiRecipientCollection()
rec_coll.add("receiver@domain.com", "receiver", MapiRecipientType.TO)
new_cal = MapiCalendar(
    "This is Location",
    "This is Summary",
    "This is recurrence test",
    start_date,
    start_date + timedelta(hours=3),
    "organizer@domain.com",
    rec_coll
)
new_cal.recurrence = recurrence

with PersonalStorage.create("output.pst", FileFormatVersion.UNICODE) as pst:
    calendar_folder = pst.create_predefined_folder("Calendar", StandardIpmFolder.APPOINTMENTS)
    calendar_folder.add_message(new_cal)
```
