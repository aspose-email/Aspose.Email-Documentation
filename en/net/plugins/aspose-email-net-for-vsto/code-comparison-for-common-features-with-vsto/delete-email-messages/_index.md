---
title: Delete Email Messages
type: docs
weight: 100
url: /net/delete-email-messages/
---


## **VSTO**
Below is the code to delete messages using VSTO Outlook.

``` cs

  // Create Application class and get namespace

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Get Inbox information in objec of type MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.Delete();      

```
## **Aspose.Email**
Below is the code to delete messages using aspose.email for .NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Create instance of ExchangeClient class by giving credentials

 ExchangeClient client = new ExchangeClient(MailBoxURI, UserName, Password, Domain);

 // Call ListMessages method to list messages info from Inbox

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 // Get URI of Message to Delete

 string MessageURI= msgCollection[0].UniqueUri;

 // Delete the message

 client.DeleteMessage(MessageURI);

```
## **Download Source Code**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Download Running Example**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)
