---
title: "Trabalhando com Contatos no Exchange Server usando WebDav"
url: /pt/java/trabalhando-com-contatos-no-exchange-server-usando-webdav/
weight: 120
type: docs
---


{{% alert color="primary" %}} 

Este artigo explica como recuperar informações de contato diretamente de um Exchange Server. Este artigo também mostra como você pode listar contatos da pasta de Contatos.

{{% /alert %}} 
## **Obtendo Contatos de um Exchange Server**
O método [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) da classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) pode ser usado para obter informações de contato de um Exchange Server. O método [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) requer o URI da pasta de Contatos, que pode ser facilmente obtido com a propriedade [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)).

Para obter contatos de um Exchange Server:

1. Inicialize a classe ExchangeClient com endereço e credenciais.
1. Obtenha o URI da pasta de Contatos com a propriedade ExchangeClient.getMailboxInfo().getContactsUri().
1. Chame o método listContacts(). Ele retorna um array de MapiContact.
1. Faça um loop foreach no array MapiContact para ler as informações de contato.

O seguinte trecho de código mostra como usar a classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) para ler todos os contatos de um Exchange Server.


~~~Java
String mailboxURI = "http://ex2003/exchange/administrator"; // WebDAV
String username = "administrator";
String password = "pwd";
String domain = "domain.local";

// Credenciais para se conectar ao Exchange Server
NetworkCredential credential = new NetworkCredential(username, password, domain);
ExchangeClient client = new ExchangeClient(mailboxURI, credential);

// Liste todos os contatos
MapiContact[] contacts = client.listContacts(client.getMailboxInfo().getContactsUri());
for (MapiContact contact : contacts)
{
    // Nome e endereço de e-mail
    System.out.println("Nome: " + contact.getNameInfo().getDisplayName() + ", Endereço de E-mail: " + contact.getElectronicAddresses().getEmail1());
}
~~~