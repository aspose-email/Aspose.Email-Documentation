---
title: Working with Outlook Calendar Items in Aspose.Email for C++
ArticleTitle: Working with Outlook Calendar Items
linktitle: Working with Outlook Calendar Items
type: docs
weight: 80
url: /cpp/working-with-outlook-calendar-items/
description: Manage Outlook calendar items in C++: create and save events, set reminders, handle attachments, and read meeting attendee status.
---

**Aspose.Email for C++** provides the [MapiCalendar](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_calendar/) class to create, edit, and manage Microsoft Outlook calendar items. You can work with reminders, attachments, meeting recipient status, and time zones programmatically.

## **Create and Save Calendar Items (ICS)**

The following code sample demonstrates how to create a calendar appointment and save it as an ICS file using Aspose.Email for C++.

1. First, a new appointment is initialized with specific details including location, subject, description, start time, and end time. 2. Then it is saved in the standard iCalendar format that can be imported into various calendar applications.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Save Calendar as MSG**

The following code sample demonstrates how to save a calendar appointment as a MSG file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

## **Add a Display Reminder**

The following code sample demonstrates how to create a calendar appointment with a reminder and save it as an ICS file. 

1. First, an appointment request is created and converted to a MAPI calendar item setting reminder properties (including a 45-minute advance notification).
2. Then the appointment is saved in iCalendar format.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

## **Add an Audio Reminder**

The following code sample demonstrates how to create a calendar appointment with a custom audio reminder and save it as an ICS file. 

1. First, an appointment request is created and converted to a MAPI calendar item, configuring reminder properties including a 58-minute advance notification with a custom sound file.
2. Then the appointment is saved in iCalendar format with the audio alert specification.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

## **Add and Retrieve Attachments**

The following code sample demonstrates how to create a calendar appointment with multiple file attachments, save it as an ICS file, and then load it back to verify the attachments. 

1. Create an appointment.
2. Add multiple document and image attachments from the file system.
3. Save the appointment with attachments in iCalendar format.
4. Then reload the saved appointment and enumerate through the attached files to confirm they were properly preserved.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

## **Check Recipient Status in Meeting Requests**

The following code sample demonstrates how to read and display the tracking status for all recipients in an Outlook message file. 

1. A MAPI message is first loaded from a file.
2. Then, it iterates through each recipient to retrieve and print their individual response status (such as None, Tentative, Accepted, or Declined) for meeting requests or voting responses.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

## **Create MapiCalendarTimeZone from System Time Zone**

The following code sample demonstrates how to create a [MapiCalendarTimeZone](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_calendar_time_zone/) object using the local system timezone information.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Set Reminders Using VALARM Tags**

The following code sample demonstrates how to create a calendar appointment with multiple types of advanced reminders. It shows how to configure four different reminder types with various trigger conditions and behaviors:

- An **audio alarm** that triggers at a specific time and repeats 4 times at 15-minute intervals with a custom sound file
- A **display alarm** that triggers 30 minutes before the event start and repeats 2 times at 15-minute intervals with a custom message
- An **email reminder** that triggers 2 days before the event and sends an email to specified attendees with subject, body, and attachment
- A **procedural alarm** that triggers at a specific date/time and repeats 23 times at hourly intervals, invoking an executable program


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}

The code illustrates complex reminder configuration including absolute and relative triggers, repetition patterns, different reminder actions, and attachment handling, then saves the complete appointment with all reminders to an ICS file.