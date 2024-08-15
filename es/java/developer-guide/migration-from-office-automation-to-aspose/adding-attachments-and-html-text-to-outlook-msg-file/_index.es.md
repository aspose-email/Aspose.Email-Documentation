---
title: "Agregar archivos adjuntos y texto HTML al archivo MSG de Outlook"
url: /es/java/adding-attachments-and-html-text-to-outlook-msg-file/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Nuestros consejos de migración muestran cómo se pueden usar los productos de Aspose para mejorar sus aplicaciones y liberarlo de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo crear un archivo MSG con el cuerpo en formato HTML y agregarle varios archivos adjuntos:

- Una sección del código de VBA que usa [Automatización de Microsoft Office](#office-automation) para crear el archivo MSG con archivos adjuntos y cuerpo HTML.
- Lo mismo que se logra usando [Aspose.Email para Java](#asposeemail-for-java).

{{% /alert %}}
## **Automatización de oficinas**
Con este método, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código de VBA. El siguiente fragmento de código crea un archivo MSG de Outlook con archivos adjuntos y cuerpo HTML.

**VBA**

~~~cs

 ' Create an object of type Outlook.Application

Set objOutlookApplication = CreateObject("Outlook.Application")

' Create an object of type olMailItem

Set objMsg = objOutlookApplication.CreateItem(olMailItem)

' Set properties of the message file e.g. subject, body and to address

' Set subject

objMsg.Subject = "This MSG file is created using Automatización de oficinas."

' Set to (recipient) address

objMsg.To = "to@domain.com"

' Set body of the email message

objMsg.HTMLBody = "<html><p>This MSG file is created using VBA code.</p>"

' Add attachments to the message

objMsg.Attachments.Add "C:\test.bmp"

objMsg.Attachments.Add "C:\test2.jpg"

' Save as Outlook MSG file

objMsg.SaveAs ("c:\testvba.msg")

' Open the MSG file

objMsg.Display


~~~
## **Aspose.Email para Java**
El siguiente fragmento de código usa la biblioteca Aspose.Email para Java para crear un archivo MSG, similar a [el creado arriba](#office-automation), con varios archivos adjuntos y cuerpo HTML. Como Aspose.Email para Java está escrito exclusivamente en Java, no se requiere la interoperabilidad COM. Además, Microsoft Outlook 2003/2007 no tiene que estar instalado en la máquina. El método que se describe a continuación es adecuado cuando Microsoft Outlook no está instalado o cuando desea generar archivos MSG en un servidor.

Los fragmentos de código siguientes muestran cómo realizar la misma tarea en Java con Aspose.Email para Java:

~~~Java

// Create an instance of type MailMessage
MailMessage msg = new MailMessage();

// Set properties of message like subject, to and HTML body
// Set subject
msg.setSubject("This MSG file is created using Aspose.Email for .NET");

// Set from (sender) address
msg.setSender(new MailAddress("from@domain.com", "From Name"));

// Set to (recipient) address and name
msg.getTo().addItem(new MailAddress("to@domain.com", "To Name"));

// Set HTML body of the email message
msg.setHtmlBody("<html><p>This MSG file is created using Java code.</p>"
        + "<p>Microsoft Outlook does not need to be installed on the machine running this code.</p>"
        + "<p>This method is suitable for creating MSG files on the server side.</html>");

// Add attachments to the message file
msg.getAttachments().addItem(new Attachment("C:\\test.bmp"));
msg.getAttachments().addItem(new Attachment("C:\\test2.jpg"));

// Save as Outlook MSG file
String strSaveFile = "C:\\TestAspose.msg";

msg.save(strSaveFile, SaveOptions.getDefaultMsgUnicode());

~~~
