---
title: Working with Outlook Calendar Items using C++ Email Library
ArticleTitle: Working with Outlook Calendar Items using C++ Email Library
linktitle: Working with Outlook Calendar Items
type: docs
weight: 80
url: /cpp/working-with-outlook-calendar-items/
description: Using C++ Email Library API, you can create and save Outlook calendar items as MSG, add and retrieve attachments from calendar files, and set reminder with appointments by adding tags.
---

## **Working with MapiCalendar**
Aspose.Email's MapiCalendar class provides methods and attributes to set various properties of a calendar item. This article provides code samples for:

- Creating and saving calendar items
- Setting reminders for MapiCalendar items
- Add/Retrieve Attachments from Calendar
- Retrieving Status of Recipients from Meeting Requests
- Creating MapiCalendar TimeZone object from Standard Timezone

### **Creating and Saving Calendar items**
The following code snippet shows you how to create and save a calendar item in ICS format with C++ Email Parser Library or API.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Saving the Calendar item as MSG**
The following code snippet shows you how to save the calendar item as MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Adding display reminder to a Calendar**
The following code snippet shows you how to add display reminder to a calendar.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Adding audio reminder to a Calendar**
The following code snippet shows you how to add audio reminder to a calendar.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Add/Retrieve attachments from Calendar files**
The following code snippet shows you how to add/retrieve attachments from calendar files.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Status of Recipients from a Meeting Request**
The following code snippet shows you how to status of recipients from a meeting request.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Create MapiCalendarTimeZone from Standard Timezone**
The following code snippet shows you how to Create MapiCalendarTimeZone from standard Timezone.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Setting Reminder with the Created Appointment**
A reminder can be added when an appointment is created. These alarms can trigger based on different criteria like n minutes before the schedule starts, repeat n times at n intervals. Different tags can be used to create these triggers in the script enclosed by BEGIN:VALARM and END:VALARM within an appointment. There are a number of variants in which the reminder can be set on an appointment.

### **Setting a Reminder by Adding Tags**
The following code snippet shows you how to Set a reminder by adding tags.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}
