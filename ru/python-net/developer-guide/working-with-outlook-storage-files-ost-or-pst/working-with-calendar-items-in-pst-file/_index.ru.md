---
title: "Работа с элементами календаря в PST-файле"
url: /ru/python-net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Добавление MapiCalendar в PST**
В статье "Создание нового PST-файла и добавление подпапок" описано, как создать PST-файл и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiCalendar в подкаталог Календара PST-файла, который вы создали или загрузили. Ниже приведены шаги для добавления MapiCalendar в PST:

1. Создайте объект MapiCalendar.
1. Установите свойства MapiCalendar с помощью конструктора и методов.
1. Создайте PST с помощью метода PersonalStorage.create().
1. Создайте предопределенную папку (Календарь) в корне PST-файла, получив доступ к корневой папке, а затем вызвав метод add_mapi_message_item().

Следующий код показывает, как создать MapiCalendar, а затем добавить его в папку календаря вновь созданного PST-файла.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Сохранение элементов календаря из PST на диск в формате ICS**
Данная статья показывает, как получить доступ к элементам календаря из PST-файла Outlook и сохранить календарь на диск в формате ICS. Используйте классы PersonalStorage и MapiCalendar для получения информации о календаре. Ниже приведены шаги для сохранения элементов календаря:

1. Загрузите PST-файл в класс PersonalStorage.
1. Просмотрите папку Календарь.
1. Получите содержимое папки Календарь, чтобы получить коллекцию сообщений.
1. Пройдитесь по коллекции сообщений.
1. Вызовите метод PersonalStorage.extract_message(), чтобы получить контактную информацию в классе MapiCalendar.
1. Вызовите метод MapiCalendar.save(), чтобы сохранить элемент календаря на диск в формате ICS.

Программа ниже загружает PST-файл с диска и сохраняет все элементы календаря в формате ICS. Файлы ICS затем могут использоваться в любой другой программе, которая может загрузить стандартный файл календаря ICS. Открытый в Microsoft Outlook, файл ICS выглядит как на скриншоте ниже.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
Следующий код показывает, как экспортировать элементы календаря из PST Outlook в формат ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Сохранение в формате ICS с оригинальной меткой времени**

Метод *keep_original_date_time_stamp* класса [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) позволяет сохранять оригинальные метки времени элементов календаря при сохранении их в файл ICS (iCalendar). Следующий пример кода демонстрирует реализацию этого метода:

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
## **Изменение/удаление вхождений из повторений**

Исключения могут быть добавлены к существующим повторениям с использованием API Aspose.Email для .NET. Следующий пример кода иллюстрирует использование этой функции.

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

# добавление одного исключения
exception_info = MapiCalendarExceptionInfo()
exception_info.location = "Лондон"
exception_info.subject = "Тема"
exception_info.original_start_date = exception_date
exception_info.start_date_time = exception_date
exception_info.end_date_time = exception_date + timedelta(hours=5)
pattern.exceptions.append(exception_info)
pattern.modified_instance_dates.append(exception_date)
# каждая измененная копия также должна иметь запись в поле DeletedInstanceDates с оригинальной датой экземпляра.
pattern.deleted_instance_dates.append(exception_date)

# добавление одного удаленного экземпляра
pattern.deleted_instance_dates.append(exception_date + timedelta(days=2))

rec_coll = MapiRecipientCollection()
rec_coll.add("receiver@domain.com", "receiver", MapiRecipientType.TO)
new_cal = MapiCalendar(
    "Это местоположение",
    "Это резюме",
    "Это тест повторения",
    start_date,
    start_date + timedelta(hours=3),
    "organizer@domain.com",
    rec_coll
)
new_cal.recurrence = recurrence

with PersonalStorage.create("output.pst", FileFormatVersion.UNICODE) as pst:
    calendar_folder = pst.create_predefined_folder("Календарь", StandardIpmFolder.APPOINTMENTS)
    calendar_folder.add_message(new_cal)
```