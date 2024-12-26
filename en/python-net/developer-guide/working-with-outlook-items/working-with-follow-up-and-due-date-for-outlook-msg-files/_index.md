---
title: Working with Follow Up and Due Date for Outlook MSG Files
ArticleTitle: Working with Follow Up and Due Date for Outlook MSG Files
type: docs
weight: 50
url: /python-net/working-with-follow-up-and-due-date-for-outlook-msg-files/
---


A follow up flag marks an email message for some kind of action. Microsoft Outlook lets users flag messages and, in the flag set-up, assign a due date for the follow up. Microsoft Outlook sends a reminder to the recipient to prompt them to follow up the email. Flagging emails and setting due dates programmatically lets software developers automate certain types of emails and help recipients remember to take action. For example, it could be used to send monthly messages to a sales team to remind them to complete their reports; or to send a message to all staff to remind them of a company meeting. Aspose.Email for .NET supports setting follow up flag and due date for the MapiMessage objects using FollowUpManager and FollowUpOptions. There are a number of variants in which the follow up flag can be set on a message. They are all used in the code sample below:

1. Set a follow up flag for a message
1. Add a due date and reminder date to a message
1. Add a flag to a recipient's message.
1. Mark as complete.
1. Remove flag.
1. Read follow up options.

## **Setting a FollowUp flag**

The following code snippet shows you how to set a followUp flag.

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Define follow-up options
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Follow Up", dt_start_date, dt_due_date, dt_reminder_date)

# Set follow-up options for the MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Save the MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Setting Follow Up for Recipients**
The following code snippet shows you how to set follow Up for recipients.

```py
import aspose.email as ae
from datetime import datetime

# Create a new MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "This message will test if follow-up options can be added to a new MAPI message."

# Convert MailMessage to MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Mark the message as draft
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Add the follow-up flag for recipients
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Follow up", dt_reminder_date)

# Save the MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Marking a FollowUp flag as Completed**

The following code snippet shows you how to mark followUp flag as completed.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Mark the message as completed
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Save the updated MapiMessage
mapi_message.save("MarkedCompleted_out.msg")
```
## **Removing a FollowUp flag**
The following code snippet shows you how to remove followUp flag.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Clear the follow-up flag
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Save the updated MapiMessage
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Read followup flag options for a message**

The following code snippet shows you how to read followup flag options for a message.

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Get the follow-up options
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```
