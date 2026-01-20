---
title: Managing Outlook Calendar Items
ArticleTitle: Managing Outlook Calendar Items
type: docs
weight: 80
url: /python-net/managing-outlook-calendar-items/
---

The [MapiCalendar](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/) class in the Aspose.Email library offers various methods and attributes to configure and manipulate calendar items. This allows for effective management of Outlook calendar items, enhancing productivity and organization. Below are the sections that will guide you through different aspects of managing calendar items.

## **Creating and Saving Calendar Items**

### **Create and Save Calendar Items**

The following code snippet demonstrates how to create and save a calendar item in ICS format:

1. Define the path where your calendar file will be stored.
2. Create an appointment by initializing a new [MapiCalendar](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/) object with specific details such as location, subject, description, start, and end times.
3. Save the created appointment as an ICS file in the specified directory.

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

### **Save Calendar Items as MSG**

The following code snippet shows you how to save the calendar item as MSG:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Set Product ID for MapiCalendar to ICS Conversion**

The Aspose.Email library allows you to save a MapiCalendar (a calendar item) to an ICS (iCalendar) file with specific options. The following [properties](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#properties) will allow you to retain the original date and time stamps associated with the calendar item and set the product identifier in the ICS file, for example to "Foo Ltd", respectively:
- *ics_save_options.keep_original_date_time_stamp*
- *ics_save_options.product_identifier* 

The product identifier is a field that identifies the software or service that generated the ICS file.

Here's a code sample that allows you to set a product ID when saving MapiCalendar to ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```

### **Count Total Calendar Events**

The [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) class provides functionality to read and analyze calendar data from a designated file. By initializing a CalendarReader object, you can extract crucial details such as the total count of events, the calendar version, the method employed, and whether the calendar includes multiple events. Below is a code snippet that illustrates how to interact with calendar data and load appointments as a comprehensive list of events: 

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"Calendar contains {reader.count} events")
print(f"The Version of the calendar is {reader.version}")
print(f"The Method of the calendar is {reader.method}")
print(f"Is calendar contains contains multiple events? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Add Display Reminders to Calendar Items**

The following code snippet shows you how to add display reminder to a calendar.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}

### **Add Audio Reminders to Calendar Items**

The following code snippet shows you how to add audio reminder to a calendar.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

## **Set the MapiCalendar State Explicitly**

Aspose.Email provides a method to explicitly define the state of a MapiCalendar object, overriding the default behavior:

- [void MapiCalendar.set_state_forced(MapiCalendarState state)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendar/#methods) - offers greater control over the calendar item's state, especially when working with received meeting requests.

When a MapiCalendar object is created, it is automatically assigned the state MapiCalendarState.Meeting. When the item is received by a recipient, the state typically changes to MapiCalendarState.Received, and the message class is updated to "IPM.Schedule.Meeting.Request".

The following code sample demonstrates how to create a meeting appointment using Aspose.Email for Python via .NET, set the organizer and calendar state manually, and save the appointment as an Outlook .msg file:


```py
from aspose.email import MapiCalendar, MapiCalendarState, MapiElectronicAddress, AppointmentSaveFormat
from datetime import datetime, timezone

# Create a MapiCalendar appointment
appointment = MapiCalendar(
    "LAKE ARGYLE WA 6743",                     # Location
    "Appointment",                             # Subject
    "This is a very important meeting :)",     # Body
    datetime(2024, 5, 10, 12, 30, 0, tzinfo=timezone.utc),  # Start time (UTC)
    datetime(2024, 5, 10, 13, 30, 0, tzinfo=timezone.utc)   # End time (UTC)
)

# Set the organizer
appointment.organizer = MapiElectronicAddress()
appointment.organizer.email_address = "test@aaa.com"
appointment.organizer.display_name = "test display Name"

# Forcefully set the calendar state to Meeting | Received
appointment.set_state_forced(MapiCalendarState.Meeting | MapiCalendarState.Received)

# Save the appointment to a .msg file
appointment.save("appointment.msg", AppointmentSaveFormat.MSG)
```

By calling the `set_state_forced`, you can manually set the calendar item's state to a specific value (e.g., MapiCalendarState.Received). This is particularly useful when you want to:

- Simulate a received meeting request.

- Preserve organizer and meeting metadata when saving the appointment to an .MSG file.

- Customize calendar workflows where the default behavior is not sufficient.

>**Note:** Manually setting the state with `set_state_forced` may impact Outlook behavior, such as the ability to forward or resend the meeting. Therefore, it should be used with caution and only when necessary for your application's logic.

## **Calendar File Management**

### **Add or Retrieve Attachments from Calendar Files**

Aspose.Email Calendar ("ae.calendar") module also provides the functionality to add and retrieve attachment information. 

**To include an attachment with the appointment**, follow the steps below:

1. Create an [Attachment]() object providing the file path. 
2. Append this attachment to the appointment list of attachments. 
3. Save the appointment to a specific file path in the iCalendar format using the [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method and the appropriate file format.

**To retrieve attachments from an appointment**, take the following steps:

1. Load an appointment from the saved file using the [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method.
2. Retrieve the number of attachments in the appointment using the *.attachments.length* property.
3. Iterate through each attachment.
4. Print the name of each attachment using the *.name* property within the loop.

The code snippet below demonstrates how to create appointments with attachments, save them, and retrieve attachment information using the "ae.calendar" module. It highlights the functionality and capabilities of working with appointments and attachments in a calendar application. 

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

### **Retrieve Recipient Status from Meeting Requests**

Aspose.Email allows you to work with meeting requests, represented as a MapiCalendar object, and retrieve the recipient status (attendance tracking) from such meeting requests. The following code snippet shows you how to identify the status of the email for each recipient:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Convert EML Appointments to MSG while Preserving HTML Body**

Aspose.Email makes it possible to convert EML appointment to MSG and preserve HTML Body. The *forced_rtf_body_for_appointment* property of the [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) class is used to manipulate the type of the appointment body. When set to *True*, the body is converted to RTF format by default. To retain the body in HTML format, it should be set to *False*. The following code sample shows how to preserve HTML body of the appointment when converting it from EML to MSG:

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
