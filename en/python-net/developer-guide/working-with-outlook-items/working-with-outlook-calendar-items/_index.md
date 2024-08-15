---
title: Working with Outlook Calendar Items
type: docs
weight: 80
url: /python-net/working-with-outlook-calendar-items/
---


## **Working with MapiCalendar**
Aspose.Email's MapiCalendar class provides methods and attributes to set various properties of a calendar item.

### **Creating and Saving Calendar items**
The following code snippet shows you how to create and save a calendar item in ICS format.

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
### **Saving the Calendar item as MSG**
The following code snippet shows you how to save the calendar item as MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Setting a Product ID when Saving MapiCalendar to ICS**

The Aspose.Email library allows you to save a MapiCalendar (a calendar item) to an ICS (iCalendar) file with specific options. With *ics_save_options.keep_original_date_time_stamp* and *ics_save_options.product_identifier* properties you can retain the original date and time stamps associated with the calendar item and set the product identifier in the ICS file, for example to "Foo Ltd", respectively. The product identifier is a field that identifies the software or service that generated the ICS file.

Here's a code sample that allows you to set a product ID when saving MapiCalendar to ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Getting total number of events**

The functionality of the [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) class allows you to read calendar data from a specified file. By creating a CalendarReader object, we can extract important information such as the total number of events, the calendar version, the method used, and whether the calendar contains multiple events. The following code snippet demonstrates how to work with calendar data and, additionally, load the appointments from the calendar as a list of multiple events. 

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"Calendar contains {reader.count} events")
print(f"The Version of the calendar is {reader.version}")
print(f"The Method of the calendar is {reader.method}")
print(f"Is calendar contains contains multiple events? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Adding display reminder to a Calendar**
The following code snippet shows you how to add display reminder to a calendar.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Adding audio reminder to a Calendar**
The following code snippet shows you how to add audio reminder to a calendar.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Add/Retrieve attachments from Calendar files**

Aspose.Email Calendar ("ae.calendar") module also provides the functionality to add and retrieve attachment information. 

- To include an attachment with the appointment, an "Attachment" object is created, providing the file path. This attachment is then appended to the appointment's list of attachments. The appointment is saved to a specific file path in the iCalendar format using the [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method and the appropriate file format.

- To retrieve attachments from an appointment, it is first loaded from the saved file using the [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method, the number of attachments present in "appointment2" are displayed, and by iterating over the attachments their names are printed.

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
### **Status of Recipients from a Meeting Request**
The following code snippet shows you how to status of recipients from a meeting request.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Convert EML Appointment to MSG preserving the Body in HTML format**

Aspose.Email makes it possible to convert EML appointment to MSG and preserve HTML Body. The "forced_rtf_body_for_appointment" property of the [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) class is used to manipulate the type of the appointment body. When set to *True*, the body is converted to RTF format by default. To retain the body in HTML format, it should be set to *False*. The following code sample shows how to preserve HTML body of the appointment when converting it from EML to MSG:

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