---
title: "Agregando Archivos Adjuntos y Texto HTML a un Archivo MSG de Outlook"
url: /es/java/adding-attachments-and-html-text-to-outlook-msg-file/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

Nuestros consejos de migración muestran cómo los productos de Aspose pueden ser utilizados para mejorar tus aplicaciones y liberarte de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo crear un archivo MSG con un cuerpo en formato HTML y agregar múltiples archivos adjuntos a él:

- Una sección de código VBA que utiliza [Microsoft Office Automation](#office-automation) para crear el archivo MSG con archivos adjuntos y un cuerpo en HTML.
- Lo mismo logrado utilizando [Aspose.Email para Java](#asposeemail-for-java).

{{% /alert %}} 
## **Automatización de Office**
Usando este método, Microsoft Outlook debe estar instalado en la máquina donde se ejecuta el código VBA. El fragmento de código a continuación crea un archivo MSG de Outlook con archivos adjuntos y cuerpo en HTML.

**VBA**

~~~cs

 ' Crear un objeto de tipo Outlook.Application

Set objOutlookApplication = CreateObject("Outlook.Application")

' Crear un objeto de tipo olMailItem

Set objMsg = objOutlookApplication.CreateItem(olMailItem)

' Establecer propiedades del archivo de mensaje e.j. asunto, cuerpo y dirección de destinatario

' Establecer asunto

objMsg.Subject = "Este archivo MSG se crea utilizando la automatización de Office."

' Establecer dirección de (destinatario)

objMsg.To = "to@domain.com"

' Establecer cuerpo del mensaje de correo electrónico

objMsg.HTMLBody = "<html><p>Este archivo MSG se crea utilizando código VBA.</p>"

' Agregar archivos adjuntos al mensaje

objMsg.Attachments.Add "C:\test.bmp"

objMsg.Attachments.Add "C:\test2.jpg"

' Guardar como archivo MSG de Outlook

objMsg.SaveAs ("c:\testvba.msg")

' Abrir el archivo MSG

objMsg.Display


~~~
## **Aspose.Email para Java**
El fragmento de código a continuación utiliza la biblioteca Aspose.Email para Java para crear un archivo MSG, similar a [el creado arriba](#office-automation), con múltiples archivos adjuntos y cuerpo en HTML. Dado que Aspose.Email para Java está escrito exclusivamente en Java, no se requiere interoperabilidad COM. Además, no es necesario que Microsoft Outlook 2003/2007 esté instalado en la máquina. El método descrito a continuación es adecuado cuando Microsoft Outlook no está instalado o cuando deseas generar archivos MSG en un servidor.

Los fragmentos de código a continuación muestran cómo realizar la misma tarea en Java utilizando Aspose.Email para Java:

~~~Java

// Crear una instancia de tipo MailMessage
MailMessage msg = new MailMessage();

// Establecer propiedades del mensaje como asunto, para y cuerpo HTML
// Establecer asunto
msg.setSubject("Este archivo MSG se crea utilizando Aspose.Email para .NET");

// Establecer dirección de (remitente)
msg.setSender(new MailAddress("from@domain.com", "Nombre del Remitente"));

// Establecer dirección y nombre de (destinatario)
msg.getTo().addItem(new MailAddress("to@domain.com", "Nombre del Destinatario"));

// Establecer cuerpo HTML del mensaje de correo electrónico
msg.setHtmlBody("<html><p>Este archivo MSG se crea utilizando código Java.</p>" 
        + "<p>No es necesario que Microsoft Outlook esté instalado en la máquina que ejecuta este código.</p>"
        + "<p>Este método es adecuado para crear archivos MSG en el lado del servidor.</html>");

// Agregar archivos adjuntos al archivo de mensaje
msg.getAttachments().addItem(new Attachment("C:\\test.bmp"));
msg.getAttachments().addItem(new Attachment("C:\\test2.jpg"));

// Guardar como archivo MSG de Outlook
String strSaveFile = "C:\\TestAspose.msg";

msg.save(strSaveFile, SaveOptions.getDefaultMsgUnicode());

~~~
