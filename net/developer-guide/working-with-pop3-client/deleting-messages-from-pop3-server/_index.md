---
title: Deleting Messages from POP3 Server
type: docs
weight: 20
url: /net/deleting-messages-from-pop3-server/
---


Aspose.Email is a robust component that allows performing customized operations after certain actions. Aspose.Email fires many events upon which users can perform operations. This feature provides users more control over their application. For example, users can perform their desired actions when:

- All bulk emails have been sent.
- A message is about to send.
- An email is completely sent.
- When a recipient is rejected by the SMTP server.

POP3 mailboxes reside on a POP3 server. The email in these mailboxes can be retrieved to your PC by [Aspose.Email.Pop3.Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client). The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) class uses POP3 protocol to copy the mail messages from your POP3 mailbox to your PC. Once the mail has been retrieved you do not need to be connected to the internet while it is being read as you could read the retrieved mail on your PC. If you don't need or want a copy of some mail messages kept on the POP3 server, you then delete it. This section shows how to delete emails using [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) class.
## **Delete an Email by Index**
The following code snippet deletes all the mail messages of a mailbox one by one, based on its index. Index should never be <=0 in [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/deletemessage/index).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}
## **Delete All Emails**
We might also call [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/deletemessages) to delete all the messages. The following code snippet shows you how to delete all emails.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteAllEmails-DeleteAllEmails.cs" >}}



If the connection to the POP3 server is broken immediately after delete operations, you can no longer call [Pop3Client](https://reference.aspose.com/error/404?path=email/net/aspose.email.pop3/pop3client).CancelDeletes() to do the things you want.
## **Cancel Deletes**
[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/undeletemessages/index) can be used to cancel the deletion of email messages. The following code snippet shows you how to cancel deletes.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-CancelDeletes-CancelDeletes.cs" >}}
