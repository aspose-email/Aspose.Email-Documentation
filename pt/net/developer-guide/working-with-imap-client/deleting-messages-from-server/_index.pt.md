---
title: "Excluindo Mensagens do Servidor"
url: /pt/net/deleting-messages-from-server/
weight: 50
type: docs
---


## **Excluindo Mensagens**

A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) pode excluir mensagens de um servidor IMAP. A função [DeleteMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) da classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) é utilizada para excluir mensagens. Ela recebe o número de sequência da mensagem ou um ID único como parâmetro. A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece os métodos [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessage/#deletemessage/) e [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) para excluir mensagens uma a uma ou múltiplas. O seguinte trecho de código mostra como excluir uma mensagem de email com o ID da mensagem 1 de um servidor IMAP.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SecurityOptions = SecurityOptions.SSLImplicit;

// Anexar mensagem de teste
client.SelectFolder(ImapFolderInfo.InBox);

var eml = new MailMessage("from@from.com", "to@to.com")
{
  Subject = "Mensagem para excluir",
  Body = "Ei! Esta mensagem será excluída!"
};
var emlId = client.AppendMessage(eml);

// Excluir mensagem anexada
client.DeleteMessage(emlId);
client.CommitDeletes();
```

## **Excluindo Múltiplas Mensagens**

Vários e-mails podem ser excluídos da caixa de entrada usando o [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) da API Aspose.Email. O método [DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletemessages/#deletemessages/) fornece várias opções para excluir múltiplas mensagens do servidor usando IDs únicos, números de sequência ou elementos da [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/). O seguinte trecho de código mostra como excluir várias mensagens.

```csharp
using var client = new ImapClient("host", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
            
// Anexar mensagens de teste
var emlList = new List<MailMessage>();
{
  var eml = new MailMessage("from@from.com", "to@to.com")
  {
    Subject = $"Mensagem para excluir {i}",
    Body = "Ei! Esta mensagem será excluída!"
  };
                
  emlList.Add(eml);
}

var appendMessagesResult = client.AppendMessages(emlList);
            
// Excluir em massa mensagens anexadas
client.DeleteMessages(appendMessagesResult.Succeeded.Values, true);
client.CommitDeletes();
```