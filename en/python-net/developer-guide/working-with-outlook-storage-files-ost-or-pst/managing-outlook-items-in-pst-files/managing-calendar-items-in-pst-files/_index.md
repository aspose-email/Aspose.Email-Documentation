---
title: Managing Calendar Items in PST Files
ArticleTitle: Managing Calendar Items in PST Files
type: docs
weight: 50
url: /python-net/managing-calendar-items-in-pst-file/
---


## **Add Calendar Events to PST Files**

[Create New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) demonstrated how to create a PST file and include subfolders within it. With Aspose.Email, you can also add a MapiCalendar to the Calendar subfolder of an existing or newly created PST file. Below are the steps to add a MapiCalendar to a PST file:

1. Create a [MapiCalendar](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/) object.
1. Set the MapiCalendar properties using a constructor and methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method.
1. Create a pre-defined folder (Calendar) at the root of the PST file by accessing the root folder and then calling the *add_mapi_message_item()* method.

The following code snippet shows you how to create a MapiCalendar and then add it to the calendar folder of a newly created PST file:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}

## **Save Outlook Calendar Items as ICS Files**

This article explains how to access calendar items from an Outlook PST file and save them to disk in ICS format. You’ll need to use the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/) classes to retrieve the calendar data. Follow these steps to save calendar items:

1. Load the PST file using the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/) class.
2. Navigate to the Calendar folder.
3. Retrieve the message collection from the Calendar folder.
4. Loop through the message collection.
5. Use the [PersonalStorage.extract_message()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method to obtain contact information in the [MapiCalendar](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/) class.
6. Use the [MapiCalendar.save()](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/#methods) method to save each calendar item to disk in ICS format.

The program below loads a PST file from disk and saves all calendar items in ICS format. These ICS files can then be used in any other program that supports standard ICS calendar files. When opened in Microsoft Outlook, an ICS file appears as shown in the screenshot below.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |

The following code snippet demonstrates how to export calendar items from an Outlook PST to ICS format:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Save ICS Files with Original Timestamps**

The *keep_original_date_time_stamp* method of the [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) class allows to preserve the original date and time stamps of the calendar items when saving them as an ICS (iCalendar) file. The following code sample demonstrates the implementation of this method:

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

## **Modify or Delete Recurrence Occurrences in PST Files**

You can add exceptions to existing recurrence patterns or delete specific occurrences in PST files using the Aspose.Email for .NET API. The following code sample demonstrates how to make such modifications:  

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
