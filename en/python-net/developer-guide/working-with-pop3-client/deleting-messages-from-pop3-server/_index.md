---
title: Deleting Emails from POP3 Server in Python
ArticleTitle: Deleting Messages from POP3 Server
type: docs
weight: 20
url: /python-net/delete-email-from-pop3-server-python/
---

Aspose.Email for .NET provides complete control over managing messages on a POP3 server. Using the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/) class, developers can connect to a mailbox and programmatically perform numerous tasks on the messages from the server including deleting specific messages or all of them. This is particularly useful in server-side mail processing applications where email cleanup is required after retrieval or based on custom logic.

This article explains how to delete messages using Aspose.Email POP3 client in different scenarios.

## **Delete Email by Index**

The following code snippet shows how to delete all message in a mailbox one by one, based on their index. The index number should never be <=0 in Pop3Client.DeleteMessage.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-DeleteEmailByIndex-DeleteEmailByIndex.py" >}}

## **Delete All Emails**

It is also possible to call `delete_messages()` method to delete all the messages. The following code snippet shows you how to use this method:


```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Delete all the messages
client.delete_messages()
```

If the connection to the POP3 server is lost immediately after the deletion operation, the `undelete_messages()` method can no longer be called to restore data.

## **Cancel Deletion Operations**

The method `undelete_messages` can be used to cancel the deletion of email messages. The following code snippet shows you how to use this method:


```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Cancel deletes
client.undelete_messages()
```
