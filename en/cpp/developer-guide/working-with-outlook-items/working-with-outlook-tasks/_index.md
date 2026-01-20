---
title: Create, Save, and Read Outlook Tasks in C++
ArticleTitle: Create, Save, and Read Outlook Tasks in C++
type: docs
weight: 110
url: /cpp/create-read-outlook-mapi-tasks/
description: Create, save, and load Outlook tasks in MSG format using the MapiTask class in C++ with Aspose.Email.
---


**Aspose.Email for C++** enables developers to create, modify, and read Microsoft Outlook tasks programmatically. The [MapiTask](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_task/) class offers properties such as `PercentComplete`, `EstimatedEffort`, `ActualEffort`, `History`, `LastUpdate`, and more, allowing you to fully define task details.

This article explains how to create, save, and read Outlook tasks, including handling VToDo tasks, reminders, attachments, and recurrence patterns.

## **Create and Save an Outlook Task**

To build a task and store it in MSG format, follow the steps below:

1. Instantiate a [MapiTask](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_task/) object.
2. Set the desired task properties.
3. Save the task to disk.


The following code sample demonstrates how to create a detailed Outlook task with comprehensive properties and save it as a MSG file  using Aspose.Email for C++. It shows how to configure task attributes including title, description, start/due dates, progress tracking (20% complete), effort estimates, ownership information, assignment history, categorization, sensitivity settings, status marking, and additional organizational fields like companies, categories, mileage, and billing information.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}


## **Read a MapiTask from Disk**

A task saved as an MSG file can be loaded using https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/, then cast to [MapiTask](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_task/).

The following code sample demonstrates how to load a task from an Outlook MSG file and convert it to a [MapiTask](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_task/) object to access task-specific properties and functionality.


```cpp
System::SharedPtr<MapiMessage> msg = MapiMessage::FromFile(dataDir + L"Task.msg");
System::SharedPtr<MapiTask> mapiTask = System::DynamicCast<Aspose::Email::Outlook::MapiTask>(msg->ToMapiMessageItem());
```


## **Load a VToDo Task (iCalendar)**

Aspose.Email allows you to load tasks exported as VToDo (.ics) files (such as Google Tasks).

The following code sample demonstrates how to convert a vCalendar VTODO task from an ICS file to an Outlook MSG task format.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}


## **Add Reminder Information to a Task**

Similar to Microsoft Outlook, Aspose.Email can add reminder information to a MapiTask.

The following code sample demonstrates how to create an Outlook task with reminder functionality and custom audio notification.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}


## **Add Attachments to a Task**

The following code sample demonstrates how to create an Outlook task with a text file attachment and save it as an MSG file


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}


## **Add Recurrence to a Task**

[MapiTask](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_task/) supports daily, weekly, monthly, and yearly recurrence patterns.

The following code sample demonstrates how to create recurring Outlook tasks with different recurrence patterns using Aspose.Email for C++. It shows how to configure four types of recurrence patterns for a task: daily recurrence that repeats every day, weekly recurrence that repeats every Wednesday, monthly recurrence that repeats on the 30th day of each month, and yearly recurrence that repeats every 12 months for 10 occurrences. The code illustrates setting various recurrence properties including pattern type, period, end conditions, day specifications, and occurrence counts, then saving the tasks in MSG format.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}
