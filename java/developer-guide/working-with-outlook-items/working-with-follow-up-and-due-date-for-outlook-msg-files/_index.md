---
title: Working with Follow Up and Due Date for Outlook MSG Files
type: docs
weight: 50
url: /java/working-with-follow-up-and-due-date-for-outlook-msg-files/
---


## **Setting Follow Up and Due Date for Outlook MSG Files**
A follow-up flag marks an email message for some kind of action. Microsoft Outlook lets users flag messages and, in the flag set-up, assign a due date for the follow-up. Microsoft Outlook sends a reminder to the recipient to prompt them to follow up the email. Flagging emails and setting due dates programmatically lets software developers automate certain types of emails and help recipients remember to take action. For example, it could be used to send monthly messages to a sales team to remind them to complete their reports; or to send a message to all staff to remind them of a company meeting. Aspose.Email for Java supports setting follow-up flag and due date for the [MapiMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage) objects using [FollowUpManager](https://apireference.aspose.com/java/email/com.aspose.email/FollowUpManager) and [FollowUpOptions](https://apireference.aspose.com/java/email/com.aspose.email/FollowUpOptions). There are a number of variants in which the follow-up flag can be set on a message. They are all used in the code sample below:

1. Set a follow-up flag for a message
1. Add a due date and reminder date to a message
1. Add a flag to a recipient's message.
1. Mark as complete.
1. Remove flag.
1. Read follow up options.
### **Setting a FollowUp flag**
The following code snippet shows you how to set a follow-up flag.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");
MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 14, 40, 0);
Date dtStartDate = calendar.getTime();

calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

calendar.add(Calendar.DATE, 1);
Date dtDueDate = calendar.getTime();

FollowUpOptions options = new FollowUpOptions("Follow Up", dtStartDate, dtDueDate, dtReminderDate);
FollowUpManager.setOptions(mapi, options);
mapi.save(dataDir + "SetFollowUpflag_out.msg");
~~~
### **Setting Follow Up for Recipients**
The following code snippet shows you how to set follow-up for recipients.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMsg = new MailMessage();
mailMsg.setSender(new MailAddress("AETest12@gmail.com"));
mailMsg.getTo().addMailAddress(new MailAddress("receiver@gmail.com"));
mailMsg.setBody("This message will test if follow up options can be added to a new mapi message.");

MapiMessage mapi = MapiMessage.fromMailMessage(mailMsg);
mapi.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT); // mark this message as draft

Calendar calendar = Calendar.getInstance();
calendar.set(2013, Calendar.MAY, 23, 16, 40, 0);
Date dtReminderDate = calendar.getTime();

// Add the follow up flag for recipient now
FollowUpManager.setFlagForRecipients(mapi, "Follow up", dtReminderDate);
mapi.save(dataDir + "SetFollowUpForRecipients_out.msg");
~~~
### **Marking a FollowUp flag as Completed**
The following code snippet shows you how to mark the follow-up flag as completed.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.markAsCompleted(mapi);
mapi.save(dataDir + "MarkedCompleted_out.msg");
~~~
### **Removing a FollowUp flag**
The following code snippet shows you how to remove the follow-up flag.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.clearFlag(mapi);
mapi.save(dataDir + "FollowUpFlagRemoved_out.msg");
~~~
### **Read followup flag options for a message**
The following code snippet shows you how to read follow-up flag options for a message.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpOptions options = FollowUpManager.getOptions(mapi);
~~~
