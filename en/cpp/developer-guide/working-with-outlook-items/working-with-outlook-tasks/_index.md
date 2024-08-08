---
title: Working with Outlook Tasks
type: docs
weight: 110
url: /cpp/working-with-outlook-tasks/
---

## **Creating, Saving and Reading Tasks**
Aspose.Email for C++ allows you to create Outlook tasks and save them to MSG format. The MapiTask class provides a number of properties such as Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a MapiTask from disc. To create and save a task to disc:

1. Instantiate a new object of the MapiTask class.
1. Enter task property information.
1. Save the task to disc in MSG format.

The following code snippet shows you how to create, save and read Tasks.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Reading a MapiTask**
The MapiTask class object is used to cast the MapiMessage object that loads a task from disc as MSG format. The following code snippet shows you how to reading a MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Reading a VToDo Task**
Google Tasks exported in iCalendar format as VToDo events can be loaded using the MapiTask class as shown in the following code sample. The following code snippet shows you how to reading a VToDo Task.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Adding Reminder Information to a MapiTask**
Similar to Microsoft Outlook, Aspose.Email can add reminder information to a MapiTask. The following code snippet shows you how to adding reminder information to a MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Adding Attachments to a MapiTask**
The following code snippet shows you how to add attachments to a MapiTask.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Adding Recurrence to MapiTask**
Aspose.Email allows to create a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code snippet shows you how to creating a task with different recurrence types.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}
