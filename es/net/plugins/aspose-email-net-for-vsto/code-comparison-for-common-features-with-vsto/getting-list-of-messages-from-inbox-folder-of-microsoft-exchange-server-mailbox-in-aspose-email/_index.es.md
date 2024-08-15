---
title: "Obtener la lista de mensajes de la carpeta Bandeja de entrada del buzón de Microsoft Exchange Server en Aspose.Email"
url: /es/net/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox-in-aspose-email/
weight: 150
type: docs
---


Para usar objetos de automatización de oficina para Microsoft Outlook, añada al proyecto referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop for Outlook. Microsoft Office Outlook también debe estar instalado en la máquina en la que se ejecuta el código.
## **VSTO**
``` cs

 // Create Application class and get namespace

Outlook.Application outlook = new Outlook.Application();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Get Inbox information in objec of type MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Unread emails

int unread = inbox.UnReadItemCount;

// Display the subject of emails in the Inbox folder

foreach (Outlook.MailItem mail in inbox.Items)

{

	Console.WriteLine(mail.Subject);

}

```
## **Aspose.Email**
Sin embargo, no es necesario instalar Microsoft Outlook en la máquina en la que se ejecuta el código. Consulte el archivo Aspose.Email.dll para compilar y ejecutar el proyecto correctamente.

``` cs

 // Create instance of ExchangeClient class by giving credentials

ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username",

				"username", "password", "domain");

// Call ListMessages method to list messages info from Inbox

ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Loop through the collection to display the basic information

foreach (ExchangeMessageInfo msgInfo in msgCollection)

{

	Console.WriteLine("Subject: " + msgInfo.Subject);

	Console.WriteLine("From: " + msgInfo.From.ToString());

	Console.WriteLine("To: " + msgInfo.To.ToString());

	Console.WriteLine("Message ID: " + msgInfo.MessageId);

	Console.WriteLine("Unique URI: " + msgInfo.UniqueUri);

	Console.WriteLine("==================================");

}

```
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772942)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Getting.List.of.Messages.from.Inbox.of.Microsoft.Mailbox.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip)
