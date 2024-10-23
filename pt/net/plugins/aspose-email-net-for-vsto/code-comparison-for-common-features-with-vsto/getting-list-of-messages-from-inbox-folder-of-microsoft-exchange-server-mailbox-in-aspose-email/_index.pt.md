---
title: "Obtendo Lista de Mensagens da Pasta de Caixa de Entrada do Microsoft Exchange Server Mailbox no Aspose.Email"
url: /pt/net/obtendo-lista-de-mensagens-da-pasta-de-caixa-de-entrada-do-microsoft-exchange-server-mailbox-no-aspose-email/
weight: 150
type: docs
---

Para usar objetos de Automação do Office para o Microsoft Outlook, adicione referências às bibliotecas Microsoft Office e Microsoft Office Interop para Outlook ao projeto. O Microsoft Office Outlook também deve estar instalado na máquina em que o código é executado.
## **VSTO**
``` cs

 // Criar a classe Application e obter o namespace

Outlook.Application outlook = new Outlook.Application();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Obter informações da Caixa de Entrada como objeto do tipo MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Emails não lidos

int unread = inbox.UnReadItemCount;

// Exibir o assunto dos emails na pasta da Caixa de Entrada

foreach (Outlook.MailItem mail in inbox.Items)

{

	Console.WriteLine(mail.Subject);

}

```
## **Aspose.Email**
No entanto, o Microsoft Outlook não precisa estar instalado na máquina onde o código é executado. Referencie o Aspose.Email.dll para compilar e executar o projeto com sucesso.

``` cs

 // Criar instância da classe ExchangeClient fornecendo credenciais

ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username",

				"username", "password", "domain");

// Chamar o método ListMessages para listar as informações das mensagens da Caixa de Entrada

ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Percorrer a coleção para exibir as informações básicas

foreach (ExchangeMessageInfo msgInfo in msgCollection)

{

	Console.WriteLine("Assunto: " + msgInfo.Subject);

	Console.WriteLine("De: " + msgInfo.From.ToString());

	Console.WriteLine("Para: " + msgInfo.To.ToString());

	Console.WriteLine("ID da Mensagem: " + msgInfo.MessageId);

	Console.WriteLine("URI Única: " + msgInfo.UniqueUri);

	Console.WriteLine("==================================");

}

```
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772942)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Getting.List.of.Messages.from.Inbox.of.Microsoft.Mailbox.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip)