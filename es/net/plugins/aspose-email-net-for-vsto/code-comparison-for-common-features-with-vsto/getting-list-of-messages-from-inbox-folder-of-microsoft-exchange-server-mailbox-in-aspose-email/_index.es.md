---
title: "Obtener lista de mensajes de la carpeta de bandeja de entrada del buzón de Microsoft Exchange Server en Aspose.Email"
url: /es/net/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox-in-aspose-email/
weight: 150
type: docs
---

Para utilizar objetos de automatización de Office para Microsoft Outlook, agregue referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook al proyecto. Microsoft Office Outlook también debe estar instalado en la máquina donde se ejecute el código.
## **VSTO**
``` cs

 // Crear clase Application y obtener namespace

Outlook.Application outlook = new Outlook.Application();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Obtener información de la bandeja de entrada en objeto de tipo MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Correos electrónicos no leídos

int unread = inbox.UnReadItemCount;

// Mostrar el asunto de los correos electrónicos en la carpeta de entrada

foreach (Outlook.MailItem mail in inbox.Items)

{

	Console.WriteLine(mail.Subject);

}

```
## **Aspose.Email**
Sin embargo, Microsoft Outlook no necesita estar instalado en la máquina donde se ejecute el código. Referencie el Aspose.Email.dll para construir y ejecutar el proyecto con éxito.

``` cs

 // Crear instancia de la clase ExchangeClient proporcionando credenciales

ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username",

				"username", "password", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada

ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para mostrar la información básica

foreach (ExchangeMessageInfo msgInfo in msgCollection)

{

	Console.WriteLine("Asunto: " + msgInfo.Subject);

	Console.WriteLine("De: " + msgInfo.From.ToString());

	Console.WriteLine("Para: " + msgInfo.To.ToString());

	Console.WriteLine("ID de mensaje: " + msgInfo.MessageId);

	Console.WriteLine("URI única: " + msgInfo.UniqueUri);

	Console.WriteLine("==================================");

}

```
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772942)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Getting.List.of.Messages.from.Inbox.of.Microsoft.Mailbox.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Getting%20List%20of%20Messages%20from%20Inbox%20of%20Microsoft%20Mailbox%20\(Aspose.Email\).zip)