---
title: Deleting Messages from POP3 Server
ArticleTitle: Deleting Messages from POP3 Server
type: docs
weight: 20
url: /python-net/deleting-messages-from-pop3-server/
---

Aspose.Email.Mail is a robust component that allows performing customized operations after certain actions. Aspose.Email.Mail fires many events upon which users can perform operations. This feature provides users more control over their application. For example, users can perform their desired actions when:

- All bulk emails have been sent.
- A message is about to send.
- An email is completely sent.
- When a recipient is rejected by SMTP server.

POP3 mailboxes reside on a POP3 server. The email in these mailboxes can be retrieved to your PC by Aspose.Email.Pop3.Pop3Client. Pop3Client Namespace uses POP3 protocol to copy the mail messages from your POP3 mailbox to your PC. Once the mail has been retrieved you do not need to be connected to the internet while it is being read as you could read the retrieved mail on your PC. If you don't need or want a copy of some mail messages kept on the POP3 server, you then delete it. This section shows how to delete emails using Pop3Client Namespace.
## **Delete an Email by Index**
The following code snippet deletes all the mail message of a mail box one by one, based on its index. Index should never be <=0 in Pop3Client.DeleteMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-DeleteEmailByIndex-DeleteEmailByIndex.py" >}}
## **Delete All Emails**
We might also call Pop3Client.DeleteAllMessages() to delete all the messages. The following code snippet shows you how to delete all emails.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Delete all the messages
client.delete_messages()
```



If the connection to the POP3 server is broken immediately after delete operations, you can no longer call Pop3Client.CancelDeletes() to do the things you want.
## **Cancel Deletes**
Pop3Client.UndeleteMessages can be used to cancel the deletion of email messages. The following code snippet shows you how to cancel deletes.



```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Cancel deletes
client.undelete_messages()
```
