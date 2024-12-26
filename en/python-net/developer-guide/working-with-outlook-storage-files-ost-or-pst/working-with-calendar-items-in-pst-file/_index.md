---
title: Working with Calendar Items in PST File
ArticleTitle: Working with Calendar Items in PST File
type: docs
weight: 50
url: /python-net/working-with-calendar-items-in-pst-file/
---


## **Adding MapiCalendar to PST**
Create a New PST File and Add Subfolders showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add MapiCalendar to the Calendar subfolder of a PST file that you have created or loaded. Below are the steps to add MapiCalendar to a PST:

1. Create a MapiCalendar object.
1. Set the MapiCalendar properties using a constructor and methods.
1. Create a PST using the PersonalStorage.create() method.
1. Create a pre-defined folder (Calendar) at the root of the PST file by accessing the root folder and then calling the add_mapi_message_item() method.

The following code snippet shows you how to create a MapiCalendar and then add it to the calendar folder of a newly created PST file.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Save Calendar Items from PST to Disk in ICS Format**
This articles shows how to access calendar items from an Outlook PST file and save the calendar to disk in ICS format. Use the PersonalStorage and MapiCalendar classes to get the calendar information. Below are the steps to save calendar items :

1. Load the PST file in the PersonalStorage class.
1. Browse the Calendar folder.
1. Get the contents of the Calendar folder to get the message collection.
1. Loop through the message collection.
1. Call PersonalStorage.extract_message() method to get the contact information in the MapiCalendar class.
1. Call the MapiCalendar.save() method to save the calendar item to disk in ICS format.

The program below loads a PST file from disk and saves all the calendar items in ICS format. The ICS files can then be used in any other program that can load the standard ICS calendar file. Opened in Microsoft Outlook, an ICS file looks like the one in the below screenshot.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
The following code snippet shows you how to export the calendar items from Outlook PST to ICS format.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Saving as ICS with Original Timestamp**

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
## **Modify/Delete Occurrences from Recurrences**

Exceptions can be added to existing recurrences using Aspose.Email for .NET API. Following code sample illustrates the usage of this feature.  

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
