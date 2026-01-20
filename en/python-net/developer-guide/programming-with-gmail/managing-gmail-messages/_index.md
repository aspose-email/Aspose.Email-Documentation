---
title: Managing Gmail Messages in Python
ArticleTitle: Managing Gmail Messages with IGmailClient in Python
type: docs
weight: 10
url: /python-net/gmail-client-email-management/
---


Aspose.Email for Python via .NET provides extended capabilities for working with Gmail accounts through the [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class) class. This includes listing, sending, appending, fetching, and deleting messages, as well as managing Gmail filters.

Before using [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class), authenticate using your client ID, client secret, refresh token, and email address. Then create a Gmail client instance:

```py
from aspose.email.clients.google import GmailClient

client = GmailClient.get_instance(client_id, client_secret, refresh_token, email)
```

## **Send Email using the Gmail API**

To send an email with an attachment through a Gmail account, use the `send_message` method of the [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class) class.

The following code sample demonstrates how to create and send an email with an attachment using the Gmail API:

```py
from aspose.email import MailMessage, Attachment

# Create the message
message = MailMessage("sender@example.com", "recipient@example.com", "Weekly Report", "Attached is the weekly report.")

# Add an attachment
attachment_path = "path/to/report.pdf"
message.attachments.add(Attachment(attachment_path))

# Send the message
message_id = client.send_message(message)
print(f"Message with attachment sent! ID: {message_id}")
```

## **Append a Message to a Gmail Folder**

To add messages directly to a Gmail mailbox, bypassing standard classification, use the following methods:

- [append_message(msg)](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#methods) for default behavior.
- [append_message(msg, label_name)](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#methods) to specify a custom label.

The code sample below demonstrates how to create an email message and append it to the recipient's inbox with a specific label using the Gmail client:

```py
message = MailMessage("sender@example.com", "recipient@example.com", "Subject for inbox message", "Body of the message")

# Append the message to the inbox with a label
message_id = client.append_message(message, "INBOX")
print(f"Message appended to the Inbox. ID: {message_id}")
```

## **List Gmail Messages**

You can retrieve a list of all messages in a Gmail mailbox using the `list_messages()` method of the [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class) class. Each item in the returned list is a [GmailMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.google/gmailmessageinfo/) object containing lightweight metadata such as *'id'* and *'thread_id'*.

The code sample below demonstrates how to retrieve and display information about all Gmail messages in the user's inbox:

```py
# List all Gmail messages
messages = client.list_messages()

# Print basic info for each message
for i, msg_info in enumerate(messages):
    print(f"Message {i + 1}: ID = {msg_info.id}, Thread ID = {msg_info.thread_id}")
```

## **Fetch Gmail Message Content**

After retrieving message metadata, use `fetch_message(message_id)` to download the full content of a specific message as a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) object. This allows access to subject, body, attachments, and other message details.

The code sample below demonstrates how to fetch and display the content of the first three Gmail messages from the user's inbox:

```py
# Fetch and display content for the first 3 messages
for i in range(min(3, len(messages))):
    message = client.fetch_message(messages[i].id)
    print(f"Message {i + 1}")
    print("Subject:", message.subject)
    print("Body:", message.body)
```

## **Delete Gmail Messages**

Use the `delete_message(message_id, move_to_trash)` method of the [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class) class to delete a message. You can either move it to the trash (non-permanent) or delete it immediately and permanently by omitting the second parameter or passing False.

The code sample below demonstrates how to move the first three messages from a list of messages (such as emails) to the trash:

```py
# Move the first 3 messages to trash
for i in range(min(3, len(messages))):
    client.delete_message(messages[i].id, True)  # True = move to trash
    print(f"Message {i + 1} moved to trash.")
```

## **Manage Gmail Filters**

Aspose.Email for Python provides the following methods of the [IGmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients.google/igmailclient/#igmailclient-class) class to automate the process of setting up a filter to organize incoming emails based on their subject line and manage existing filters in a Google email account:

- `list_filters()` - Retrieves all filters applied to the mailbox.
- `create_filter(filter)` - Adds a new filter with custom criteria and actions.
- `get_filter(id)` - Fetches specific filter details.
- `delete_filter(id)` - Removes filters permanently.

### **Create and List Gmail Filters**

The following code sample demonstrates how to create and manage an email filter using the Aspose.Email library specifically for Google client:

```py
from aspose.email.clients.google.filters import Filter, Criteria, Action

# Create a new filter
filter_obj = Filter()
filter_obj.matching_criteria = Criteria()
filter_obj.matching_criteria.subject = "Important"

filter_obj.action = Action()
filter_obj.action.add_label_ids = ["IMPORTANT"]

# Create the filter
filter_id = client.create_filter(filter_obj)
print(f"Filter created! ID: {filter_id}")

# List all filters
filters = client.list_filters()
for f in filters:
    print(f"Filter ID: {f.id}")
```

### **Delete Gmail Filters**

The following code sample demonstrates how to remove all filters from the Gmail account:

```py
filters = client.list_filters()

# Delete each filter
for f in filters:
    client.delete_filter(f.id)
    print(f"Filter ID: {f.id} deleted.")
```
