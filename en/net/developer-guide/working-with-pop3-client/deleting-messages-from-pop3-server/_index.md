---
title: Delete Emails from POP3 Server
ArticleTitle: Delete Emails from POP3 Server
type: docs
weight: 60
url: /net/delete-emails-from-pop3-server/
---

## **Deleting Emails from Server**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class uses POP3 protocol to copy the mail messages from mailbox to your PC. Once the mail has been retrieved you do not need to be connected to the internet while it is being read as you could read the retrieved mail on PC. If you don't need or want a copy of some mail messages kept on the POP3 server, you then delete it. This section shows how to delete emails using [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

### **Delete Email by Index**

The following code snippet deletes all the mail messages of a mailbox one by one, based on its index. Index should never be <=0 in [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

### **Delete All Emails**

We might also call [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/) to delete all the messages. The following code snippet shows you how to delete all emails.

```cs
// Delete all the messages
client.DeleteMessages();
```

If the connection to the POP3 server is broken immediately after deleting operations, you can no longer call Cancel Deletes to do the things you want.

### **Cancel Email Deletions**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) can be used to cancel the deletion of email messages. The following code snippet shows you how to cancel deletes.

```cs
// Cancel deletes
client.UndeleteMessages();
```
