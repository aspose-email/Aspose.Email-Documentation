---
title: "Creando un archivo de mensaje de Outlook (MSG) en Aspose.Email"
url: /es/net/creating-an-outlook-message-msg-file-in-aspose-email/
weight: 90
type: docs
---


Para usar la automatización de Office, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código. También se requiere una referencia a Outlook.interop.dll.
### **VSTO**
``` cs

 // Crea una nueva instancia de la aplicación Outlook

Outlook.Application objOutlook = new Outlook.Application();

// Creando un nuevo mensaje de Outlook desde la instancia de la aplicación Outlook

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Establecer información del destinatario

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Establecer el asunto del mensaje

msgInterop.Subject = "Asunto";

// Establecer algún texto HTML en el cuerpo HTML

msgInterop.HTMLBody = "<h3>Encabezado HTML 3</h3> <u>Este es un texto subrayado</u>";

// Guardar el archivo MSG en el disco local

string strMsg = "TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);


```
### **Aspose.Email**
Los ejemplos a continuación utilizan Aspose.Email para crear el archivo MSG de Outlook. Está escrito en .NET puro y no utiliza COM Interop. La instalación de Outlook no es necesaria para crear el archivo msg de esta manera.

``` cs

 // Crear una instancia de la clase Aspose.Email.MailMessage

MailMessage msg = new MailMessage();

// Establecer la información de los destinatarios

msg.To = "to@domain.com";

msg.CC = "cc@domain.com";

// Establecer el asunto

msg.Subject = "Asunto";

// Establecer el cuerpo HTML

msg.HtmlBody = "<h3>Encabezado HTML 3</h3> <u>Este es un texto subrayado</u>";

// Agregar un archivo adjunto

msg.Attachments.Add(new Attachment("image.bmp"));

// Guardarlo en el disco local

string strMsg = "TestAspose.msg";

msg.Save(strMsg, MessageFormat.Msg);

```
## **Descargar código de ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772940)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)