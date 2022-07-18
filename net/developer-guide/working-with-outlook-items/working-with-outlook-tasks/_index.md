---
title: Working with Outlook Tasks
type: docs
weight: 100
url: /net/working-with-outlook-tasks/
---


## **Creating, Saving and Reading Tasks**
Aspose.Email for .NET allows you to create Outlook tasks and save them to MSG format. The [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask) class provides a number of properties such as [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/properties/percentcomplete), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/properties/estimatedeffort), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/properties/actualeffort), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/properties/history), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/properties/lastupdate), and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask) from disk. To create and save a task to disk:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class.
1. Enter task property information.
1. Save the task to disc in MSG format.

The following code snippet shows you how to create, save and read Tasks.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}
### **Reading a MapiTask**
The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class object is used to cast the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) object that loads a task from the disk as MSG format. The following code snippet shows you how to read a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}
### **Reading a VToDo Task**
Google Tasks exported in iCalendar format as VToDo events can be loaded using the [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask) class as shown in the following code sample. The following code snippet shows you how to read a VToDo Task.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}
### **Adding Reminder Information to a MapiTask**
Similar to Microsoft Outlook, Aspose.Email can add reminder information to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask). The following code snippet shows you how to add reminder information to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}
### **Adding Attachments to a MapiTask**
The following code snippet shows you how to add attachments to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}
### **Adding Recurrence to MapiTask**
Aspose.Email allows creating a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code snippet shows you how to create a task with different recurrence types.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}
### **Converting Task to MHT**
Aspose.Email can generate [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) like output during the conversion of a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask) to MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}
