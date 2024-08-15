---
title: "Creación de un archivo de mensajes de Outlook (MSG) en Aspose.Email"
url: /es/net/creating-an-outlook-message-msg-file-in-aspose-email/
weight: 90
type: docs
---


Para usar Office Automation, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código. También es necesaria una referencia a Outlook.Interop.dll.
### **VSTO**
``` cs

 // Creates a new Outlook Application instance

Outlook.Application objOutlook = new Outlook.Application();

// Creating a new Outlook message from the Outlook Application instance

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Set recipient information

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Set the message subject

msgInterop.Subject = "Subject";

// Set some HTML text in the HTML body

msgInterop.HTMLBody = "<h3>HTML Heading 3</h3> <u>This is underlined text</u>";

// Save the MSG file in local disk

string strMsg = "TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);


```
### **Aspose.Email**
Los ejemplos siguientes utilizan Aspose.Email para crear el archivo MSG de Outlook. Está escrito únicamente en .NET y no utiliza COM Interop. No es necesario instalar Outlook para crear el archivo msg de esta manera.

``` cs

 // Create an instance of the Aspose.Email.MailMessage class

MailMessage msg = new MailMessage();

// Set recipients information

msg.To = "to@domain.com";

msg.CC = "cc@domain.com";

// Set the subject

msg.Subject = "Subject";

// Set HTML body

msg.HtmlBody = "<h3>HTML Heading 3</h3> <u>This is underlined text</u>";

// Add an attachment

msg.Attachments.Add(new Attachment("image.bmp"));

// Save it in local disk

string strMsg = "TestAspose.msg";

msg.Save(strMsg, MessageFormat.Msg);

```
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772940)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)
