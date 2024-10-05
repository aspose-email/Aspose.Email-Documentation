---
title: Удалить электронные сообщения
type: docs
weight: 100
url: /net/delete-email-messages/
---

## **VSTO**

Ниже приведен код для удаления сообщений с использованием VSTO Outlook.

```cs

  // Создайте класс Application и получите пространство имен

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Получите информацию о папке "Входящие" в объекте типа MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.Delete();

```

## **Aspose.Email**

Ниже приведен код для удаления сообщений с использованием aspose.email для .NET.

```cs

  string MailBoxURI = "http://MachineName/exchange/Username";

 string UserName = "username";

 string Password = "password";

 string Domain = "domain";

 // Создайте экземпляр класса ExchangeClient, указав учетные данные

 ExchangeClient client = new ExchangeClient(MailBoxURI, UserName, Password, Domain);

 // Вызовите метод ListMessages, чтобы получить информацию о сообщениях из папки "Входящие"

 ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

 // Получите URI сообщения для удаления

 string MessageURI= msgCollection[0].UniqueUri;

 // Удалите сообщение

 client.DeleteMessage(MessageURI);

```

## **Скачать исходный код**

- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)

## **Скачать работающий пример**

- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)

