---
title: "Obtenga el número de correos electrónicos del buzón"
url: /es/net/get-the-number-of-emails-in-the-mailbox/
weight: 140
type: docs
---


## **VSTO**
A continuación se muestra el código para obtener los correos electrónicos en el buzón mediante VSTO Outlook.

``` cs

  // Create Application class and get namespace

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Get Inbox information in objec of type MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 int i = inbox.Items.Count;

 MessageBox.Show("Message count: " + i);

```
## **Aspose.Email**
A continuación se muestra el código para obtener los correos electrónicos en el buzón mediante aspose.email para.NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Create instance of ExchangeClient class by giving credentials

 ExchangeClient client = new ExchangeClient(MailBoxURI,UserName, Password, Domain);

 // Call ListMessages method to list messages info from Inbox

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 int i = msgCollection.Count;

 Console.WriteLine("Message count: " + i);

```
## **Descargar código fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Get%20the%20number%20of%20emails%20in%20the%20mailbox)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Running Example**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)
