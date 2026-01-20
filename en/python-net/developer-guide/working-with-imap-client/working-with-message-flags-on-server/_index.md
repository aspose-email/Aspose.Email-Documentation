---
title: Manage IMAP Message Flags in Python with Aspose.Email
ArticleTitle: Manage Message Flags on IMAP Server
type: docs
weight: 60
url: /python-net/manage-message-flags-on-imap-server/
---

Aspose.Email for Python via .NET allows you to manage IMAP message flags such as Read, Answered, Deleted, and Custom Keywords directly from your Python application. These flags help mark the state or status of email messages in the mailbox and are useful for building organized email workflows.

This article covers how to:

- Set and remove standard IMAP system flags

- Assign custom keyword flags to messages

The key [methods](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#methods) used: 

- change_message_flags()
- remove_message_flags()
- add_message_flags()

Supported Flags:

- Answered
- Deleted
- Draft
- Flagged
- IsRead
- Recent
- Custom keyword flags

## **Set IMAP Message Flags**

Use the `change_message_flags()` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to apply standard flags like IsRead or Deleted to messages. This method takes a message identifier (sequence number or UID) and one or more flags.

The following code snippet shows you how to set message flags on an IMAP server with Aspose.Email:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

## **Remove Message Flags**

You can remove system or custom flags using the `remove_message_flags()` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. This is commonly used to unmark messages as read or deleted. The code sample below demonstrates how to remove the 'is_read' flag with just a line of code:

```py
# Remove the 'is_read' flag from the message
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```

## **Add Custom Keyword Flags to IMAP Messages**

Aspose.Email also supports assigning custom keyword flags using the `add_message_flags()` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. These user-defined flags can be helpful for categorization or processing rules.  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Create a new message
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Append the message to the Inbox
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Add custom keyword flags to the message
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Verify the presence of the custom keyword
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Keyword found")
```
