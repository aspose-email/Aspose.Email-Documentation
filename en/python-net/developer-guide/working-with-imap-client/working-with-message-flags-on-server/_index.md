---
title: Working with Message Flags on Server
ArticleTitle: Working with Message Flags on Server
type: docs
weight: 60
url: /python-net/working-with-message-flags-on-server/
---


## **Changing the Message Flags**
You can change message flags by using the ChangeMessageFlags() method. This method takes two parameters.

1. The message's sequence number or unique ID.
1. MessageFlag.

The following flags can be set:

- Answered
- Deleted
- Draft
- Empty
- Flagged
- IsRead
- Recent
### **Setting Message Flags**
The following code snippet shows you how to change message flags on an IMAP server with Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Removing Message Flags**

The API also provides the 'remove_message_flags' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to remove predefined system flags such as \Seen (which corresponds to the message being read), \Answered (message has been replied to), \Flagged (message is marked as important), \Deleted (message is marked for deletion), and \Draft (message is saved as a draft), as well as custom keyword flags defined by users. The method takes the following parameters: unique identifier (UID) or sequence number of the message along with the flags you want to remove. The code sample below demonstrates how to remove the 'is_read' flag with just a line of code:

```py
# Remove the message flag
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Setting Custom Flags**
You can also set custom flags to a message using the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) of the API. Its 'add_message_flags' method provides the ability of setting custom flags on messages.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Create a message
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Append the message to mailbox
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Add custom flags to the added message
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Retreive the messages for checking the presence of custom flag
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Keyword found")
```
