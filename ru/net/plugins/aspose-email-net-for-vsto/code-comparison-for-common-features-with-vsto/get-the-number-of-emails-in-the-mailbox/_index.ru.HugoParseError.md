---
title: Получить количество электронных писем в почтовом ящике
type: docs
weight: 140
url: /net/get-the-number-of-emails-in-the-mailbox/
---


## **VSTO**
Ниже приведен код для получения электронных писем в почтовом ящике с использованием VSTO Outlook.

``` cs

  // Создание класса Application и получение пространства имен

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Получение информации о папке Входящие в объекте типа MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 int i = inbox.Items.Count;

 MessageBox.Show("Количество сообщений: " + i);

```
## **Aspose.Email**
Ниже приведен код для получения электронных писем в почтовом ящике с использованием aspose.email для .NET.

``` cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Создание экземпляра класса ExchangeClient с указанием учетных данных

 ExchangeClient client = new ExchangeClient(MailBoxURI,UserName, Password, Domain);

 // Вызов метода ListMessages для получения информации о сообщениях из папки Входящие

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 int i = msgCollection.Count;

 Console.WriteLine("Количество сообщений: " + i);

```
## **Скачать исходный код**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Get%20the%20number%20of%20emails%20in%20the%20mailbox)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Скачать работающий пример**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)