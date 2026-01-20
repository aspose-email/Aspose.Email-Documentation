---
title: Managing Outlook Tasks
ArticleTitle: Managing Outlook Tasks
type: docs
weight: 110
url: /python-net/managing-outlook-tasks/
---


## **Creating, Saving and Reading Tasks**

Aspose.Email for .NET allows you to create Outlook tasks and save them in MSG format. The [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) class provides a number of properties such as *percent_complete*, *estimated_effort*, *actual_effort*, *history*, *last_update*, and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a MapiTask from disc. 

### **Create and Save Tasks to a Disc**

The code sample below demonstrates how to create, configure, and store an Outlook task using the MAPI (Messaging Application Programming Interface):

1. Instantiate a new object of the [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) class.
1. Configure task properties.
1. Save the task to disc in MSG format.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}

### **Read MapiTask**

The [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) class is used to cast a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) object that loads a task from a disk in MSG format. The following code snippet demonstrates how to read a MapiTask:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}

### **Read VToDo Tasks**

Google Tasks exported in iCalendar format as VToDo events can be loaded using the [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) class. The following code snippet shows you how to load and read a VToDo task:

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```

### **Add Reminders to MapiTasks**

Similar to Microsoft Outlook, Aspose.Email can add reminder information to a MapiTask. The following code snippet shows you how this task can be performed with Aspose.Email for Python via .NET:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Add Attachments to MapiTasks**

Use the [add](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/#methods) method of the [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) class to add an attachment to a MapiTask. The following code sample will help you with that:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Task with attacment", "Test body of task with attacment", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("attachment data"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Add Recurrence to MapiTasks**

Aspose.Email allows to create a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code snippet shows you how to create a task with different recurrence types:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

## **Task Conversion**

### **Convert Tasks to MHT**

The following code sample demonstrates how to convert a task to MHT format specifying additional options for the [MHT format](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) when task-specific fields should be rendered (RENDER_TASK_FIELDS) and that the header information should be included (WRITE_HEADER). The [mht_format_options](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#properties) property of the [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) class is used to define additional options when saving in MHTML format.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```

