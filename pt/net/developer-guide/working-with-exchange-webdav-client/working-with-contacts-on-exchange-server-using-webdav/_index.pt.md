---
title: "Trabalhando com Contatos no Exchange Server usando WebDav"
url: /pt/net/trabalhando-com-contatos-no-exchange-server-usando-webdav/
weight: 50
type: docs
---


{{% alert color="primary" %}} 

As contas do Exchange Server contêm mais do que apenas mensagens de email. Além de [buscar](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [mover](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [enviar](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) e [deletar mensagens de email](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) de servidores Exchange, Aspose.Email permite que você trabalhe com contatos. Este artigo explica como recuperar informações de contato diretamente de um Exchange Server. Este artigo também mostra como você pode listar contatos da pasta Contatos.

{{% /alert %}} 
## **Obtendo Contatos de um Exchange Server**
O método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) da classe [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) pode ser usado para obter informações de contato de um Exchange Server. O método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) requer o URI da pasta Contatos, que pode ser facilmente obtido com a propriedade [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).

Para obter contatos de um Exchange Server:

1. Inicialize a classe [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) com o endereço e credenciais.
1. Obtenha o URI da pasta Contatos com a propriedade [ExchangeClient.MailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).
1. Chame o método [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts). Ele retorna um array de [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Faça um loop foreach no array [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact) para ler as informações de contato.

O seguinte trecho de código mostra como usar a classe [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) para ler todos os contatos de um Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}