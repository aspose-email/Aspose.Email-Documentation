---
title: "Удаление сообщений с сервера"
url: /ru/net/deleting-messages-from-server/
weight: 50
type: docs
---


## **Удаление сообщений**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс может удалять сообщения с сервера IMAP. [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) функция используется для удаления сообщений. В качестве параметра она принимает порядковый номер сообщения или уникальный идентификатор. [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) and [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) методы удаления сообщений по одному или по нескольким. В следующем фрагменте кода показано, как удалить сообщение электронной почты с идентификатором сообщения 1 с сервера IMAP.

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

## **Удаление нескольких сообщений**

Несколько писем можно удалить из почтового ящика с помощью [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API Aspose.Email. [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) метод предоставляет ряд опций для удаления нескольких сообщений с сервера с использованием уникальных идентификаторов, порядковых номеров или [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) элементы. В следующем фрагменте кода показано, как удалить несколько сообщений.


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
