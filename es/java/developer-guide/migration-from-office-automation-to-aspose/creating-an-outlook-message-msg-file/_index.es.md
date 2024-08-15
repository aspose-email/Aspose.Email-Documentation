---
title: "Creación de un archivo de mensajes de Outlook (MSG)"
url: /es/java/creating-an-outlook-message-msg-file/
weight: 20
type: docs
---


{{% alert color="primary" %}}

Nuestros consejos de migración muestran cómo se pueden usar los productos de Aspose para mejorar sus aplicaciones y liberarlo de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo crear un archivo de mensajes de Outlook (MSG) usando [Automatización de Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java). Los ejemplos de código establecen las propiedades básicas del archivo MSG (To, Cc, Subject y HTML body) antes de guardar el archivo en el disco.

{{% /alert %}}
## **Automatización de oficinas**
Para usar Automatización de oficinas, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código. También es necesaria una referencia a Outlook.Interop.dll.
### **Ejemplos de programación**
Los siguientes fragmentos de código crean un archivo MSG mediante Automatización de oficinas.

**C#**

~~~cs

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

string strMsg = @"c:\\temp\TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);



~~~
## **Aspose.Email para Java**
Los ejemplos siguientes utilizan Aspose.Email para crear el archivo MSG de Outlook. Está escrito en Java puro y no utiliza COM Interop. No se requiere la instalación de Outlook para crear el archivo msg de esta manera.

~~~Java

// Create an instance of the Aspose.Email.MailMessage class
MailMessage msg = new MailMessage();

// Set recipients information
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setCC(MailAddressCollection.to_MailAddressCollection("cc@domain.com"));

// Set the subject
msg.setSubject("Subject");

// Set HTML body
msg.setHtmlBody("<h3>HTML Heading 3</h3> <u>This is underlined text</u>");

// Add an attachment
msg.getAttachments().addItem(new Attachment("test.txt"));

// Save it in local disk
String strMsg = "c:\\ TestAspose.msg";
msg.save(strMsg, SaveOptions.getDefaultMsgUnicode());

~~~