---
title: "Eliminar mensajes del servidor"
url: /es/net/deleting-messages-from-server/
weight: 50
type: docs
---


## **Eliminar mensajes**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) la clase puede eliminar mensajes de un servidor IMAP. El [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) la función se usa para borrar mensajes. Toma el número de secuencia del mensaje o el identificador único como parámetro. El [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) provides [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) and [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) métodos para eliminar mensajes uno por uno o varios. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el identificador de mensaje 1 de un servidor IMAP.

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

## **Eliminar varios mensajes**

Se pueden eliminar varios correos electrónicos del buzón de correo mediante el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) de la API Aspose.Email. El [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) el método proporciona una serie de opciones para eliminar varios mensajes del servidor mediante identificadores únicos, números de secuencia o [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) elementos. El siguiente fragmento de código muestra cómo eliminar varios mensajes.


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
