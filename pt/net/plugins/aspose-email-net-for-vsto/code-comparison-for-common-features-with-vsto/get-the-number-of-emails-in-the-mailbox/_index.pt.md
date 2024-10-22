---
title: "Obter o número de emails na caixa de entrada"
url: /pt/net/get-the-number-of-emails-in-the-mailbox/
weight: 140
type: docs
---

## **VSTO**
Abaixo está o código para obter os emails na caixa de entrada usando VSTO Outlook.

``` cs

  // Criar classe Application e obter namespace

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Obter informações da Caixa de Entrada em objeto do tipo MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 int i = inbox.Items.Count;

 MessageBox.Show("Contagem de mensagens: " + i);

```
## **Aspose.Email**
Abaixo está o código para obter os emails na caixa de entrada usando aspose.email para .NET.

``` cs

  string MailBoxURI = "http://NomeDaMáquina/exchange/Usuário";

 string UserName = "nome_de_usuario";

 string Password = "senha";

 string Domain = "domínio";

 // Criar instância da classe ExchangeClient fornecendo credenciais

 ExchangeClient client = new ExchangeClient(MailBoxURI,UserName, Password, Domain);

 // Chamar o método ListMessages para listar informações das mensagens da Caixa de Entrada

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 int i = msgCollection.Count;

 Console.WriteLine("Contagem de mensagens: " + i);

```
## **Baixar Código Fonte**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Get%20the%20number%20of%20emails%20in%20the%20mailbox)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Baixar Exemplo em Execução**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)