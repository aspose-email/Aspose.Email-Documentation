---
title: Managing Follow-Up and Due Dates for Outlook MSG Files
ArticleTitle: Managing Follow-Up and Due Dates for Outlook MSG Files
type: docs
weight: 60
url: /net/managing-follow-up-and-due-dates-for-outlook-msg-files/
---


## **Set Follow-Up and Due Dates for MSG Files**

A follow-up flag marks an email message for some kind of action. Microsoft Outlook lets users flag messages and, in the flag set-up, assign a due date for the follow-up. Microsoft Outlook sends a reminder to the recipient to prompt them to follow up the email. Flagging emails and setting due dates programmatically lets software developers automate certain types of emails and help recipients remember to take action. For example, it could be used to send monthly messages to a sales team to remind them to complete their reports; or to send a message to all staff to remind them of a company meeting. Aspose.Email for .NET supports setting follow-up flag and due date for the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objects using [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). There is a number of variants in which the follow-up flag can be set on a message. They are all used in the code sample below:

1. Set a follow-up flag for a message
1. Add a due date and reminder date to a message
1. Add a flag to a recipient's message.
1. Mark as complete.
1. Remove flag.
1. Read follow up options.

### **Set Follow-Up Flags**

The following code snippet shows you how to set a follow-up flag.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Set Follow-Up for Recipients**

The following code snippet shows you how to set follow-up for recipients.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Mark Follow-Up Flags as Completed**

The following code snippet shows you how to mark the follow-up flag as completed.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Remove Follow-Up Flags**

The following code snippet shows you how to remove the follow-up flag.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Read Follow-Up Flag Options**

The following code snippet shows you how to read follow-up flag options for a message.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}
