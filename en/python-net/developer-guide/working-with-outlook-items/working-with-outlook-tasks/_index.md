---
title: Working with Outlook Tasks
type: docs
weight: 110
url: /python-net/working-with-outlook-tasks/
---


## **Creating, Saving and Reading Tasks**
Aspose.Email for .NET allows you to create Outlook tasks and save them to MSG format. The MapiTask class provides a number of properties such as Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a MapiTask from disc. To create and save a task to disc:

1. Instantiate a new object of the MapiContact class.
1. Enter task property information.
1. Save the task to disc in MSG format.

The following code snippet shows you how to create, save and read Tasks.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Reading a MapiTask**
The MapiContact class object is used to cast the MapiMessage object that loads a task from disc as MSG format. The following code snippet shows you how to reading a MapiTask.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Reading a VToDo Task**
Google Tasks exported in iCalendar format as VToDo events can be loaded using the MapiTask class as shown in the following code sample. The following code snippet shows you how to reading a VToDo Task.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Adding Reminder Information to a MapiTask**
Similar to Microsoft Outlook, Aspose.Email can add reminder information to a MapiTask. The following code snippet shows you how to adding reminder information to a MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Adding Attachments to a MapiTask**

Use the [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) method of the [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) class to add an attachment to a MapiTask. The following code sample will help you with that:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Task with attacment", "Test body of task with attacment", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("attachment data"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Adding Recurrence to MapiTask**
Aspose.Email allows to create a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code snippet shows you how to creating a task with different recurrence types.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Converting a Task to MHT**

The following code sample demonstrates how to convert a task to MHT format specifying additional options for the MHT format when task-specific fields should be rendered (RENDER_TASK_FIELDS) and that the header information should be included (WRITE_HEADER). The *mht_format_options* property of the [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) class is used to define additional options when saving in MHTML format.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```