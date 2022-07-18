---
title: Working with Message Flags on Server
type: docs
weight: 30
url: /net/working-with-message-flags-on-server/
---


## **Changing the Message Flags**
You can change message flags by using the [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/methods/changemessageflags/index) method. This method takes two parameters.

1. The message's sequence number or unique ID.
1. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags).

The following flags can be set:

- [Answered](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/answered)
- [Deleted](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/deleted)
- [Draft](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/draft)
- [Empty](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/empty)
- [Flagged](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/flagged)
- [IsRead](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/isread)
- [Recent](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/properties/recent)
### **Setting Message Flags**
The following code snippet shows you how to change message flags on an IMAP server with Aspose.Email.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}
### **Removing Message Flags**
Message flags can also be removed with the [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/methods/removemessageflags/index) method. Usage is similar to that of the [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/methods/changemessageflags/index) method. It takes a sequence number or unique message ID and [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags). The following code snippet shows you how to remove message flags.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}
## **Setting Custom Flags**
You can also set custom flags to a message using the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient) of the API. The ImapClient's AddMessageFlags provides the ability to set custom flags on messages.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}
