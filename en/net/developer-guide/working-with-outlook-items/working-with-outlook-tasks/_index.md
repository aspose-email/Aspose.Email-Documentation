---
title: Create, Save and Read Outlook Tasks
ArticleTitle: Create, Save and Read Outlook Tasks
type: docs
weight: 110
url: /net/working-with-outlook-tasks/
---


## **Create Outlook Tasks**

Aspose.Email for .NET allows you to create Outlook tasks and save them to MSG format. The [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) class provides a number of properties such as [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/), and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) from disk. To create and save a task to disk:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Enter task property information.
1. Save the task to disc in MSG format.

The following code snippet shows you how to create, save and read Tasks.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

## **Read MAPI Tasks**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class object is used to cast the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object that loads a task from the disk as MSG format. The following code snippet shows you how to read a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

## **Read VToDo Tasks**

Google Tasks exported in iCalendar format as VToDo events can be loaded using the [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) class as shown in the following code sample. The following code snippet shows you how to read a VToDo Task.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Add Reminder Information to MAPI Tasks**

Similar to Microsoft Outlook, Aspose.Email can add reminder information to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). The following code snippet shows you how to add reminder information to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Add Attachments to MAPI Tasks**

The following code snippet shows you how to add attachments to a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Add Recurrence to MAPI Tasks**

Aspose.Email allows creating a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code snippet shows you how to create a task with different recurrence types.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Convert Tasks to MHT**

Aspose.Email can generate [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) like output during the conversion of a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) to MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}

## **MSG to HTML Convertion Preserving Task Fields**

The [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) enumeration allows you to specify that task fields should be included in the header of the saved HTML file. The following code snippet shows how to preserve task fields in a header when saving a html file:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```
