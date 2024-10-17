---
title: "Eliminando Mensajes del Servidor"
url: /es/net/eliminando-mensajes-del-servidor/
weight: 50
type: docs
---

## **Eliminando Mensajes**

La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) puede eliminar mensajes de un servidor IMAP. La función [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se utiliza para eliminar mensajes. Toma el número de secuencia del mensaje o el ID único como parámetro. El [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona los métodos [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) y [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) para eliminar mensajes uno por uno o múltiples. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el ID de mensaje 1 de un servidor IMAP.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SecurityOptions = SecurityOptions.SSLImplicit;

// Agregar mensaje de prueba
client.SelectFolder(ImapFolderInfo.InBox);

var eml = new MailMessage("from@from.com", "to@to.com")
{
  Subject = "Mensaje a eliminar",
  Body = "¡Hola! Este mensaje será eliminado!"
};
var emlId = client.AppendMessage(eml);

//Eliminar mensaje agregado
client.DeleteMessage(emlId);
client.CommitDeletes();
```

## **Eliminando Múltiples Mensajes**

Se pueden eliminar múltiples correos electrónicos de la bandeja de entrada utilizando el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) de la API Aspose.Email. El método [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) proporciona una serie de opciones para eliminar múltiples mensajes del servidor utilizando IDs únicos, números de secuencia o elementos de [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/). El siguiente fragmento de código muestra cómo eliminar múltiples mensajes.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
            
// Agregar mensajes de prueba
var emlList = new List<MailMessage>();
{
  var eml = new MailMessage("from@from.com", "to@to.com")
  {
    Subject = $"Mensaje a eliminar {i}",
    Body = "¡Hola! Este mensaje será eliminado!"
  };
                
  emlList.Add(eml);
}

var appendMessagesResult = client.AppendMessages(emlList);
            
// Eliminación masiva de mensajes agregados
client.DeleteMessages(appendMessagesResult.Succeeded.Values, true);
client.CommitDeletes();
```