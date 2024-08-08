---
title: Deleting Messages from Server
type: docs
weight: 50
url: /net/deleting-messages-from-server/
---


## **Deleting Messages**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class can delete messages from an IMAP server. The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) function is used to delete messages. It takes the message sequence number or unique ID as a parameter. The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) and [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) methods for deleting messages one by one or multiple. The following code snippet shows you how to delete an email message with the message ID 1 from an IMAP server.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SecurityOptions = SecurityOptions.SSLImplicit;

// Append test message
client.SelectFolder(ImapFolderInfo.InBox);

var eml = new MailMessage("from@from.com", "to@to.com")
{
  Subject = "Message to delete",
  Body = "Hey! This Message will be deleted!"
};
var emlId = client.AppendMessage(eml);

// Delete appended message
client.DeleteMessage(emlId);
client.CommitDeletes();
```

## **Deleting Multiple Messages**

Multiple emails can be deleted from mailbox using the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) of Aspose.Email API. The [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) method provides a number of options to delete multiple messages from the server using unique ids, sequence numbers or [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) elements. The following code snippet shows you how to delete multiple messages.


```csharp
using var client = new ImapClient("host", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
            
// Append test messages
var emlList = new List<MailMessage>();
{
  var eml = new MailMessage("from@from.com", "to@to.com")
  {
    Subject = $"Message to delete {i}",
    Body = "Hey! This Message will be deleted!"
  };
                
  emlList.Add(eml);
}

var appendMessagesResult = client.AppendMessages(emlList);
            
// Bulk Delete appended Messages
client.DeleteMessages(appendMessagesResult.Succeeded.Values, true);
client.CommitDeletes();
```
