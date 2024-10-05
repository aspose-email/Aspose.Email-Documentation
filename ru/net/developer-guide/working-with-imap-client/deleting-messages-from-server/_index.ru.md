---
title: "Удаление сообщений с сервера"
url: /ru/net/deleting-messages-from-server/
weight: 50
type: docs
---


## **Удаление сообщений**

Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) может удалять сообщения с IMAP-сервера. Функция [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) используется для удаления сообщений. Она принимает номер последовательности сообщения или уникальный ID в качестве параметра. Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет методы [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) и [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) для удаления сообщений по одному или несколько одновременно. Следующий код показывает, как удалить электронное сообщение с ID сообщения 1 с IMAP-сервера.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SecurityOptions = SecurityOptions.SSLImplicit;

// Добавление тестового сообщения
client.SelectFolder(ImapFolderInfo.InBox);

var eml = new MailMessage("from@from.com", "to@to.com")
{
  Subject = "Сообщение для удаления",
  Body = "Привет! Это сообщение будет удалено!"
};
var emlId = client.AppendMessage(eml);

// Удаление добавленного сообщения
client.DeleteMessage(emlId);
client.CommitDeletes();
```

## **Удаление нескольких сообщений**

Несколько электронных писем можно удалить из почтового ящика с помощью [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API Aspose.Email. Метод [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) предлагает ряд вариантов для удаления нескольких сообщений с сервера, используя уникальные идентификаторы, номера последовательностей или элементы [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/). Следующий код показывает, как удалить несколько сообщений.


```csharp
using var client = new ImapClient("host", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
            
// Добавление тестовых сообщений
var emlList = new List<MailMessage>();
{
  var eml = new MailMessage("from@from.com", "to@to.com")
  {
    Subject = $"Сообщение для удаления {i}",
    Body = "Привет! Это сообщение будет удалено!"
  };
                
  emlList.Add(eml);
}

var appendMessagesResult = client.AppendMessages(emlList);
            
// Массовое удаление добавленных сообщений
client.DeleteMessages(appendMessagesResult.Succeeded.Values, true);
client.CommitDeletes();
```