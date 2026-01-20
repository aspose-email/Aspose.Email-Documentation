---
title: Working with Outlook Calendar Items
ArticleTitle: Working with Outlook Calendar Items
type: docs
weight: 120
url: /java/working-with-outlook-calendar-items/
---

## **Working with MapiCalendar**

Aspose.Email's [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) class provides methods and attributes to set various properties of a calendar item. This article provides code samples for:

- [**Working with MapiCalendar**](#working-with-mapicalendar)
  - [**Creating and Saving Calendar Items**](#creating-and-saving-calendar-items)
  - [**Saving the Calendar Item as MSG**](#saving-the-calendar-item-as-msg)
  - [**Adding Display Reminder to a Calendar**](#adding-display-reminder-to-a-calendar)
  - [**Adding Audio Reminder to a Calendar**](#adding-audio-reminder-to-a-calendar)
  - [**Add/Retrieve Attachments from Calendar Files**](#addretrieve-attachments-from-calendar-files)
  - [**Status of Recipients from a Meeting Request**](#status-of-recipients-from-a-meeting-request)
  - [**Create MapiCalendarTimeZone from Standard Timezone**](#create-mapicalendartimezone-from-standard-timezone)
- [**Setting Reminder with the Created Appointment**](#setting-reminder-with-the-created-appointment)
  - [**Setting a Reminder by Adding Tags**](#setting-a-reminder-by-adding-tags)
- [**Convert Appointment EML to MSG with HTML Body**](#convert-appointment-eml-to-msg-with-html-body)


### **Creating and Saving Calendar Items**

The following code snippet shows you how to create and save a calendar item in ICS format.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

Calendar cal = Calendar.getInstance();
cal.set(2012, Calendar.OCTOBER, 2, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2012, Calendar.OCTOBER, 2, 14, 0, 0);
Date endDate = cal.getTime();

MapiCalendar calendar = new MapiCalendar("LAKE ARGYLE WA 6743", 
                                         "Appointment", 
                                         "This is a very important meeting :)", 
                                         startDate, 
                                         endDate);

calendar.save(dataDir + "CalendarItem_out.ics", AppointmentSaveFormat.Ics);
~~~

### **Saving the Calendar Item as MSG**

The following code snippet shows you how to save the calendar item as MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~

### **Setting a product ID when saving a Calendar Item to ICS**

The [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) property of the [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) class is used to save a MAPI calendar item to an iCalendar (ICS) file preserving original date and time information as well as a custom product identifier. The property specifies the identifier for the product that created the iCalendar object.

The following code sample shows how to work with iCalendar (ICS) data within a MAPI calendar object:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
```

### **Adding Display Reminder to a Calendar**

The following code snippet shows you how to add display reminder to a calendar.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));
// Create Appointment
Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizer"), 
                                  attendees);
MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar calendar = (MapiCalendar) mapi.toMapiMessageItem();

// Set calendar Properties
calendar.setReminderSet(true);
calendar.setReminderDelta(5); // 45 min before start of event

String savedFile = (dataDir + "calendarWithDisplayReminder.ics");
calendar.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Adding Audio Reminder to a Calendar**

The following code snippet shows you how to add an audio reminder to a calendar.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));

Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizer"), 
                                  attendees);

MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar cal = (MapiCalendar) mapi.toMapiMessageItem();

cal.setReminderSet(true);
cal.setReminderDelta(58); // 58 min before start of event
cal.setReminderFileParameter(dataDir + "Alarm01.wav");

String savedFile = dataDir + "calendarWithAudioReminder_out.ics";
cal.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Add/Retrieve Attachments from Calendar Files**

The following code snippet shows you how to add/retrieve attachments from calendar files.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

String[] files = new String[3];
files[0] = "attachment_1.doc";
files[1] = "download.png";
files[2] = "Desert.jpg";

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));

Appointment app1 = new Appointment("Home", 
                                   startDate, 
                                   endDate, 
                                   new MailAddress("organizer@domain.com", "Organizer"), 
                                   attendees);
for (String file : files) {
    app1.getAttachments().addItem(new Attachment(dataDir + file));
}

app1.save(dataDir + "appWithAttachments_out.ics", AppointmentSaveFormat.Ics);

Appointment app2 = Appointment.load(dataDir + "appWithAttachments_out.ics");
System.out.println(app2.getAttachments().size());
for (Attachment att : app2.getAttachments())
    System.out.println(att.getName());
~~~

### **Status of Recipients from a Meeting Request**

The following code snippet shows you how to get the status of recipients from a meeting request.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~

### **Set Calendar Appointment State Explicitly**

Aspose.Email allows you to set the state of a [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) object explicitly, overriding the default behavior. The `setStateForced` method provides better control over calendar event states, particularly when handling received meeting requests. By default, when a meeting is created, its state is `MapiCalendarState.Meeting`. When received in a recipient’s inbox, it automatically changes to `MapiCalendarState.Received`, and its message class is updated to `IPM.Schedule.Meeting.Request`. Using `SetStateForced` allows manually setting the state to Received, which can be useful for preserving organizer information when saving the calendar as an MSG file. However, this may prevent proper forwarding or resending of the meeting.

The following code sample will help you implement this feature:

```java
Calendar c = Calendar.getInstance();
c.set(2024, Calendar.MAY, 10, 12, 30, 0);
Date startDate = c.getTime();
c.set(2024, Calendar.MAY, 10, 13, 30, 0);
Date endDate = c.getTime();
MapiCalendar appointment = new MapiCalendar(
        "LAKE ARGYLE WA 6743",
        "Appointment",
        "This is a very important meeting :)",
        startDate,
        endDate);

MapiElectronicAddress organizer = new MapiElectronicAddress();
organizer.setEmailAddress("test@aaa.com");
organizer.setDisplayName("test display Name");
appointment.setOrganizer(organizer);

appointment.setStateForced(MapiCalendarState.Meeting | MapiCalendarState.Received);

appointment.save("appointment.msg", AppointmentSaveFormat.Msg);
```

### **Create MapiCalendarTimeZone from Standard Timezone**

The following code snippet shows you how to сreate [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) from the standard Timezone.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Eastern Standard Time");
~~~

## **Setting Reminder with the Created Appointment**

A reminder can be added when an appointment is created. These alarms can trigger based on different criteria like n minutes before the schedule starts, repeat n times at n intervals. Different tags can be used to create these triggers in the script enclosed by BEGIN:VALARM and END:VALARM within an appointment. There is a number of variants in which the reminder can be set on an appointment.

### **Setting a Reminder by Adding Tags**

The following code snippet shows you how to set a reminder by adding tags.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();
long MIN_MS = 60 * 1000;
long HR_MS = 60 * MIN_MS;
long DAY_MS = 24 * HR_MS;

String location = "Meeting Location: Room 5";
Date startDate = getDate(1997, 3, 18, 18, 30, 00);
Date endDate = getDate(1997, 3, 18, 19, 30, 00);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizer");
MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("bbb@bmail.com", "First attendee"));

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

// Audio alarm that will sound at a precise time and
// Repeat 4 more times at 15 minute intervals:
AppointmentReminder audioReminder = new AppointmentReminder();
audioReminder.setTrigger(new ReminderTrigger(getDate(1997, 3, 17, 13, 30, 0)));
audioReminder.setRepeat(4);
audioReminder.setDuration(new ReminderDuration(15 * MIN_MS));
audioReminder.setAction(ReminderAction.Audio);
ReminderAttachment attach = new ReminderAttachment(new URI("ftp://Host.com/pub/sounds/bell-01.aud"));
audioReminder.getAttachments().addItem(attach);
target.getReminders().addItem(audioReminder);


// Display alarm that will trigger 30 minutes before the
// Scheduled start of the event it is
// Associated with and will repeat 2 more times at 15 minute intervals:
AppointmentReminder displayReminder = new AppointmentReminder();
ReminderDuration dur = new ReminderDuration(-30 * MIN_MS);
displayReminder.setTrigger(new ReminderTrigger(dur, ReminderRelated.Start));
displayReminder.setRepeat(2);
displayReminder.setDuration(new ReminderDuration(15 * MIN_MS));
displayReminder.setAction(ReminderAction.Display);
displayReminder.setDescription("Breakfast meeting with executive team at 8:30 AM EST");
target.getReminders().addItem(displayReminder);

// Email alarm that will trigger 2 days before the
// Scheduled due date/time. It does not
// Repeat. The email has a subject, body and attachment link.
AppointmentReminder emailReminder = new AppointmentReminder();
ReminderDuration dur1 = new ReminderDuration(-2 * DAY_MS);
emailReminder.setTrigger(new ReminderTrigger(dur1, ReminderRelated.Start));
ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");
emailReminder.getAttendees().addItem(attendee);
emailReminder.setAction(ReminderAction.Email);
emailReminder.setSummary("REMINDER: SEND AGENDA FOR WEEKLY STAFF MEETING");
emailReminder.setDescription("A draft agenda needs to be sent out to the attendees to the weekly managers meeting (MGR-LIST). Attached is a pointer the document template for the agenda file.");
ReminderAttachment attach1 = new ReminderAttachment(new URI("http://Host.com/templates/agenda.doc"));
emailReminder.getAttachments().addItem(attach1);
target.getReminders().addItem(emailReminder);

// Procedural alarm that will trigger at a precise date/time
// And will repeat 23 more times at one hour intervals. The alarm will
// Invoke a procedure file.
AppointmentReminder procReminder = new AppointmentReminder();
procReminder.setTrigger(new ReminderTrigger(getDate(1998, 1, 1, 5, 0, 0)));
procReminder.setRepeat(23);
procReminder.setDuration(new ReminderDuration(1 * DAY_MS));
procReminder.setAction(ReminderAction.Procedure);
ReminderAttachment attach2 = new ReminderAttachment(new URI("ftp://Host.com/novo-procs/felizano.exe"));
procReminder.getAttachments().addItem(attach2);
target.getReminders().addItem(procReminder);
target.save(dataDir + "savedFile_out.ics");
~~~

## **Convert Appointment EML to MSG with HTML Body**

Since version 19.3, Aspose.Email provides the ability to convert Appointment EML to MSG while retaining the HTML body of the appointment. Aspose.Email provides a [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) property which has a default value of **true.** When the value of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) is set to **true**, the appointment body is converted to RTF format. To keep the appointment body format in HTML format, set the value of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) to **false.**

The following example demonstrates the use of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) property to keep the appointment body format in HTML format.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMessage = MailMessage.load(dataDir + "TestAppointment.eml");

MapiConversionOptions conversionOptions = new MapiConversionOptions();
conversionOptions.setFormat(OutlookMessageFormat.Unicode);

// default value for ForcedRtfBodyForAppointment is true
conversionOptions.setForcedRtfBodyForAppointment(false);

MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, conversionOptions);

if (mapiMessage.getBodyType() == BodyContentType.Html) {
    System.out.println("Body Type: Html");
} else if (mapiMessage.getBodyType() == BodyContentType.Rtf) {
    System.out.println("Body Type: Rtf");
}

mapiMessage.save(dataDir + "TestAppointment_out.msg");
~~~
