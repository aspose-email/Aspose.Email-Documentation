---
title: "Agregar archivos adjuntos y texto HTML al archivo de mensajes de Outlook en Aspose.Email"
url: /es/net/adding-attachments-and-html-text-to-outlook-msg-file-in-aspose-email/
weight: 10
type: docs
---


Con este método, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código. El siguiente fragmento de código crea un archivo MSG de Outlook con archivos adjuntos y cuerpo HTML.
## **VSTO**
``` cs

 // Create an object of type Outlook.Application

Outlook.Application objOutlook = new Outlook.Application();

//Create an object of type olMailItem

Outlook.MailItem oIMailItem = objOutlook.CreateItem(Outlook.OlItemType.olMailItem);

//Set properties of the message file e.g. subject, body and to address

//Set subject

oIMailItem.Subject = "This MSG file is created using Office Automation.";

//Set to (recipient) address

oIMailItem.To = "to@domain.com";

//Set body of the email message

oIMailItem.HTMLBody = "<html><p>This MSG file is created using VBA code.</p>";

//Add attachments to the message

oIMailItem.Attachments.Add("image.bmp");

oIMailItem.Attachments.Add("pic.jpeg");

//Save as Outlook MSG file

oIMailItem.SaveAs("testvba.msg");

//Open the MSG file

oIMailItem.Display();

```
## **Aspose.Email**
El siguiente fragmento de código usa la biblioteca Aspose.Email for.NET para crear un archivo MSG, similar al creado anteriormente, con varios archivos adjuntos y cuerpo HTML. Como Aspose.Email para.NET está escrito exclusivamente en .NET, no es necesaria la interoperabilidad COM. Además, no es necesario instalar Microsoft Outlook 2003/2007 en la máquina. El método que se describe a continuación es adecuado cuando Microsoft Outlook no está instalado o cuando desea generar archivos MSG en un servidor.

Los fragmentos de código siguientes muestran cómo realizar la misma tarea en C# con Aspose.Email para .NET.

``` cs

 // Create an instance of type MailMessage

MailMessage msg = new MailMessage();

// Set properties of message like subject, to and HTML body

// Set subject

msg.Subject = "This MSG file is created using Aspose.Email for .NET";

// Set from (sender) address

msg.Sender = new MailAddress("from@domain.com", "From Name");

// Set to (recipient) address and name

msg.To.Add(new MailAddress("to@domain.com", "To Name"));

// Set HTML body of the email message

msg.HtmlBody = @"<html><p>This MSG file is created using C# code.</p>" +

	"<p>Microsoft Outlook does not need to be installed on the machine running this code.</p>" +

	"<p>This method is suitable for creating MSG files on the server side.</html>";

// Add attachments to the message file

msg.Attachments.Add(new Attachment("image.bmp"));

msg.Attachments.Add(new Attachment("pic.jpeg"));

// Save as Outlook MSG file

string strSaveFile ="TestAspose.msg";

msg.Save(strSaveFile, MessageFormat.Msg);

```
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772938)
- [Github](https://github.com/Aspose/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip)
