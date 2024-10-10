---
title: "Получение списка сообщений из папки Входящие почтового ящика Microsoft Exchange Server в Aspose.Email"
url: /ru/net/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox-in-aspose-email/
weight: 150
type: docs
---


Чтобы использовать объекты автоматизации Office для Microsoft Outlook, добавьте ссылки на библиотеки Microsoft Office и Microsoft Office Interop для Outlook в проект. Microsoft Office Outlook также должен быть установлен на машине, на которой выполняется код.
## **VSTO**
``` cs

 // Создание класса Application и получение пространства имен

Outlook.Application outlook = new Outlook.Application();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Получить информацию о Входящих в объекте типа MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Непрочитанные электронные письма

int unread = inbox.UnReadItemCount;

// Отобразить темы электронных писем в папке Входящие

foreach (Outlook.MailItem mail in inbox.Items)

{

	Console.WriteLine(mail.Subject);

}

```
## **Aspose.Email**
Тем не менее, Microsoft Outlook не нужно устанавливать на машине, где выполняется код. Ссылайтесь на Aspose.Email.dll, чтобы успешно собрать и запустить проект.

``` cs

 // Создание экземпляра класса ExchangeClient с указанием учетных данных

ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username",

				"username", "password", "domain");

// Вызов метода ListMessages для получения информации о сообщениях из Входящих

ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Цикл по коллекции для отображения основной информации

foreach (ExchangeMessageInfo msgInfo in msgCollection)

{

	Console.WriteLine("Тема: " + msgInfo.Subject);

	Console.WriteLine("От: " + msgInfo.From.ToString());

	Console.WriteLine("Кому: " + msgInfo.To.ToString());

	Console.WriteLine("ID сообщения: " + msgInfo.MessageId);

	Console.WriteLine("Уникальный URI: " + msgInfo.UniqueUri);

	Console.WriteLine("==================================");

}

```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772942)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Getting.List.of.Messages.from.Inbox.of.Microsoft.Mailbox.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip)