---
title: Working with Outlook Tasks
type: docs
weight: 90
url: /java/working-with-outlook-tasks/
---

## **Creating, Saving and Reading Outlook Tasks**

Aspose.Email for Java allows developers to create Outlook tasks and save them as MSG format. The [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class provides a number of properties such as [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--), etc., to accommodate and set information required for an Outlook task. This article shows how to create, save and read a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) from disk.

### **Create and Save a MapiTask**

The following steps can be used to create and save a Task to disk.

1. Instantiate a new object of the [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class.
1. Enter information for the task various properties.
1. Save the task to disk in MSG format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Read a MapiTask**

The [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class object is used to cast the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object that loads a task from the disk in MSG format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Read a VToDo Task**

Google Tasks exported in iCalendar format as VToDo events can be loaded using the [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) class as shown in the following code sample.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Add Reminder Information to a MapiTask**

Similar to Microsoft Outlook, Aspose.Email can add reminder information to a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). The following code snippet shows you how to add reminder information to a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Add Attachment to a MapiTask**

The following code snippet shows you how to add attachments to a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Converting Outlook Task to MHT**

Aspose.Email can generate [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) like output during the conversion of a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) to MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}
