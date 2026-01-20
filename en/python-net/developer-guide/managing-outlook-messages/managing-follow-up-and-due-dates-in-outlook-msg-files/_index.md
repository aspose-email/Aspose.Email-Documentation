---
title: Outlook MSG File Follow-Up and Due Date Management in Python
ArticleTitle: Manage Follow-Up and Due Dates in Outlook MSG Files
type: docs
weight: 70
url: /python-net/manage-follow-up-and-due-date-for-outlook-msg-files/
---


A follow-up flag marks an e-mail message for some kind of action. Microsoft Outlook allows users to flag messages and to set a due date for the follow-up when setting the flag. Microsoft Outlook sends a reminder to the recipient to prompt them to follow up on the email. By flagging emails and setting due dates programmatically, software developers can automate certain types of emails and help recipients remember to take action. For example, it could be used to send monthly messages to a sales team to remind them to complete their reports, or to send a message to all employees to remind them of a company meeting. Aspose.Email for .NET supports setting follow-up flags and due dates for the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) objects using [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/) and [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/). There is a number of ways to set the follow-up flag on a message. They are all demonstrated in the code sample below:

- Set a follow-up flag for a message
- Add a due date and reminder date to a message
- Add a flag to a recipient's message.
- Mark as complete.
- Remove flag.
- Read follow-up options.


## **Set a Follow-Up Flag**

The following code snippet shows you how to set a follow-up flag.

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

## **Add Follow-Up Flags for Recipients**

The following code snippet shows you how to create, customize, and save a MAPI email message with added follow-up options for recipients using Aspose.Email:

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

## **Mark a Follow-Up Flag as Completed**

The following code snippet shows you how to load an existing MAPI message, mark it as completed, and then save the updated message:

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Mark the message as completed
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Save the updated MapiMessage
mapi_message.save("MarkedCompleted_out.msg")
```

## **Remove a Follow-Up Flag**

The following code snippet shows you how to remove a follow-up flag:

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Clear the follow-up flag
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Save the updated MapiMessage
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Read Follow-Up Flag Options**

The following code snippet shows you how to load a MAPI email message from a file and retrieve its follow-up options:

```py
import aspose.email as ae

# Load the MapiMessage from file
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Get the follow-up options
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```

## **Set Unsent Message Flag**

The following code snippet creates an email message in draft form and marks it as ready for sending by toggling the [UNSENT](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessageflags/#members) flag.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Flagged message", "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```

## **Access Follow-Up Information in MSG Files**

### **Extract Read and Delivery Receipt Information**

The code sample below demonstrates how to extract recipient information and their track status from an Outlook message (MSG) file:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Recipient: {recipient.display_name}")
    print(f"Delivery time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Read time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```