---
title: "Excluir Mensagens de Email"
url: /pt/net/delete-email-messages/
weight: 100
type: docs
---


## **VSTO**
Abaixo está o código para excluir mensagens usando VSTO Outlook.

``` cs

  // Criar classe Application e obter namespace

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Obter informações da Caixa de Entrada em objeto do tipo MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.Delete();      

```
## **Aspose.Email**
Abaixo está o código para excluir mensagens usando aspose.email para .NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Criar instância da classe ExchangeClient fornecendo as credenciais

 ExchangeClient client = new ExchangeClient(MailBoxURI, UserName, Password, Domain);

 // Chamar o método ListMessages para listar as informações das mensagens da Caixa de Entrada

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 // Obter URI da Mensagem a ser Excluída

 string MessageURI= msgCollection[0].UniqueUri;

 // Excluir a mensagem

 client.DeleteMessage(MessageURI);

```
## **Baixar Código Fonte**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Baixar Exemplo em Execução**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)