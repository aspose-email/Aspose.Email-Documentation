---
title: Working with Outlook Calendar Items
type: docs
weight: 120
url: /net/working-with-outlook-calendar-items/
---


## **Working with MapiCalendar**

Aspose.Email's MapiCalendar class provides methods and attributes to set various properties of a calendar item. This article provides code samples for:

- [**Working with MapiCalendar**](#working-with-mapicalendar)
  - [**Creating and Saving Calendar items**](#creating-and-saving-calendar-items)
  - [**Saving the Calendar item as MSG**](#saving-the-calendar-item-as-msg)
  - [**Adding display reminder to a Calendar**](#adding-display-reminder-to-a-calendar)
  - [**Adding audio reminder to a Calendar**](#adding-audio-reminder-to-a-calendar)
  - [**Add/Retrieve attachments from Calendar files**](#addretrieve-attachments-from-calendar-files)
  - [**Status of Recipients from a Meeting Request**](#status-of-recipients-from-a-meeting-request)
  - [**Create MapiCalendarTimeZone from Standard Timezone**](#create-mapicalendartimezone-from-standard-timezone)
- [**Setting Reminder with the Created Appointment**](#setting-reminder-with-the-created-appointment)
  - [**Setting a Reminder by Adding Tags**](#setting-a-reminder-by-adding-tags)
- [**Convert Appointment EML to MSG with HTML Body**](#convert-appointment-eml-to-msg-with-html-body)
  
### **Creating and Saving Calendar items**

The following code snippet shows you how to create and save a calendar item in ICS format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Saving the Calendar item as MSG**

The following code snippet shows you how to save the calendar item as MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Setting a Product ID when Saving MapiCalendar to ICS**

The [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) property of the [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) class is used to save a MAPI calendar item to an iCalendar (ICS) file preserving original date and time information as well as a custom product identifier. The property specifies the identifier for the product that created the iCalendar object.

The following code sample shows how to work with iCalendar (ICS) data within a MAPI calendar object:

```cs
var icsSaveOptions = new MapiCalendarIcsSaveOptions
{
    KeepOriginalDateTimeStamp = true,
    ProductIdentifier = "Foo Ltd"
};

mapiCalendar.Save("my.ics", icsSaveOptions);
```
### **Getting total number of events**

The CalendarReader class enables handling calendar events effortlessly. The following properties and a method allow you to work with multiple events:

- **CalendarReader.Count** - The Count property of the CalendarReader class allows you to retrieve the number of Vevent components (events) present in the calendar, making it easier to track the total number of events.
- **CalendarReader.IsMultiEvents** - This property determines whether the calendar contains multiple events. It provides a boolean value indicating whether the calendar contains more than one event, aiding in identifying calendars with single or multiple events.
- **CalendarReader.Method** - The Method property obtains the iCalendar method type associated with the calendar object. It returns the method type, such as “REQUEST,” “PUBLISH,” or “CANCEL,” providing valuable insights into the purpose of the calendar.
- **CalendarReader.Version** - Gets the Version of iCalendar.
- **CalendarReader.LoadAsMultiple()** This method enables the loading of a list of events from a calendar containing multiple events. It returns a list of Appointment objects, allowing easy access and processing of each event individually.

The following code example demonstrates how you can implement these capabilities in your project:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("Calendar contains " + reader.Count + " events");
Console.WriteLine("The Version of the calendar is " + reader.Version);
Console.WriteLine("The Method of the calendar is " + reader.Method);
Console.WriteLine("Is calendar contains contains multiple events? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Adding display reminder to a Calendar**

The following code snippet shows you how to add a display reminder to a calendar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Adding audio reminder to a Calendar**

The following code snippet shows you how to add an audio reminder to a calendar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Add/Retrieve attachments from Calendar files**

The following code snippet shows you how to add/retrieve attachments from calendar files.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Status of Recipients from a Meeting Request**

The following code snippet shows you how to show the status of recipients from a meeting request.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Create MapiCalendarTimeZone from Standard Timezone**

The following code snippet shows you how to Create MapiCalendarTimeZone from standard Timezone.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Setting Reminder with the Created Appointment**

A reminder can be added when an appointment is created. These alarms can trigger based on different criteria like n minutes before the schedule starts, repeat n times at n intervals. Different tags can be used to create these triggers in the script enclosed by BEGIN:VALARM and END:VALARM within an appointment. There is a number of variants in which the reminder can be set on an appointment.

### **Setting a Reminder by Adding Tags**

The following code snippet shows you how to set a reminder by adding tags.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Convert Appointment EML to MSG with HTML Body**

Since version 19.3, Aspose.Email provides the ability to convert Appointment EML to MSG while retaining the HTML body of the appointment. Aspose.Email provides a [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) property which has a default value of **true.** When the value of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) is set to **true**, the appointment body is converted to RTF format. To keep the appointment body format in HTML format, set the value of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) to **false.**

The following example demonstrates the use of [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) property to keep the appointment body format in HTML format.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}
