---
title: Working with Follow Up and Due Date for Outlook MSG Files in C++
ArticleTitle: Working with Follow Up and Due Date for Outlook MSG Files in C++
linktitle: Working with Follow Up and Due Date for Outlook MSG Files
type: docs
weight: 50
url: /cpp/working-with-follow-up-and-due-date-for-outlook-msg-files/
description: Follow Up flag for Recipients and the Due Date for Outlook MSG Files can both be set or removed using the C++ Email Parser Library API.
---

## **Setting Follow Up and Due Date for Outlook MSG Files**
A follow up flag marks an email message for some kind of action. Microsoft Outlook lets users flag messages and, in the flag set-up, assign a due date for the follow up. Microsoft Outlook sends a reminder to the recipient to prompt them to follow up the email. Flagging emails and setting due dates programmatically lets software developers automate certain types of emails and help recipients remember to take action. For example, it could be used to send monthly messages to a sales team to remind them to complete their reports; or to send a message to all staff to remind them of a company meeting. Aspose.Email for C++ supports setting follow up flag and due date for the MapiMessage objects using FollowUpManager and FollowUpOptions. There are a number of variants in which the follow up flag can be set on a message. They are all used in the code sample below:

1. Set a follow up flag for a message
1. Add a due date and reminder date to a message
1. Add a flag to a recipient's message.
1. Mark as complete.
1. Remove flag.
1. Read follow up options.

### **Setting a FollowUp flag**
The following code snippet shows you how to set a followUp flag using C++ Email Parser Library API.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpflag-SetFollowUpflag.cpp" >}}

### **Setting Follow Up for Recipients**
The following code snippet shows you how to set follow Up for recipients.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cpp" >}}

### **Marking a FollowUp flag as Completed**
The following code snippet shows you how to mark followUp flag as completed.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cpp" >}}

### **Removing a FollowUp flag**
The following code snippet shows you how to remove followUp flag.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cpp" >}}

### **Read followup flag options for a message**
The following code snippet shows you how to read followup flag options for a message.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cpp" >}}
