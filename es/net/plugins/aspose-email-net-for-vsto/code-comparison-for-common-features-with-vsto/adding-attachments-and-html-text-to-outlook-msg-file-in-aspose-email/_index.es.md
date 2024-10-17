---
title: "Agregar Archivos Adjuntos y Texto HTML a un Archivo Msg de Outlook en Aspose.Email"
url: /es/net/adding-attachments-and-html-text-to-outlook-msg-file-in-aspose-email/
weight: 10
type: docs
---


Usando este método, Microsoft Outlook debe estar instalado en la máquina donde se ejecuta el código. El fragmento de código a continuación crea un archivo MSG de Outlook con archivos adjuntos y cuerpo HTML.
## **VSTO**
``` cs

 // Crear un objeto del tipo Outlook.Application

Outlook.Application objOutlook = new Outlook.Application();

//Crear un objeto del tipo olMailItem

Outlook.MailItem oIMailItem = objOutlook.CreateItem(Outlook.OlItemType.olMailItem);

//Establecer propiedades del archivo de mensaje, p. ej. asunto, cuerpo y dirección a

//Establecer asunto

oIMailItem.Subject = "Este archivo MSG se crea utilizando Office Automation.";

//Establecer la dirección de (destinatario)

oIMailItem.To = "to@domain.com";

//Establecer cuerpo del mensaje de correo electrónico

oIMailItem.HTMLBody = "<html><p>Este archivo MSG se crea utilizando código VBA.</p>";

//Agregar archivos adjuntos al mensaje

oIMailItem.Attachments.Add("image.bmp");

oIMailItem.Attachments.Add("pic.jpeg");

//Guardar como archivo MSG de Outlook

oIMailItem.SaveAs("testvba.msg");

//Abrir el archivo MSG

oIMailItem.Display();

```
## **Aspose.Email**
El fragmento de código a continuación utiliza la biblioteca Aspose.Email para .NET para crear un archivo MSG, similar al creado anteriormente, con múltiples archivos adjuntos y cuerpo HTML. Dado que Aspose.Email para .NET está escrito completamente en .NET, no se requiere interoperabilidad COM. Además, Microsoft Outlook 2003/2007 no tiene que estar instalado en la máquina. El método descrito a continuación es adecuado cuando Microsoft Outlook no está instalado o cuando desea generar archivos MSG en un servidor.

Los fragmentos de código a continuación muestran cómo realizar la misma tarea en C# utilizando Aspose.Email para .NET.

``` cs

 // Crear una instancia del tipo MailMessage

MailMessage msg = new MailMessage();

// Establecer propiedades del mensaje como asunto, para y cuerpo HTML

// Establecer asunto

msg.Subject = "Este archivo MSG se crea utilizando Aspose.Email para .NET";

// Establecer la dirección de (remitente)

msg.Sender = new MailAddress("from@domain.com", "Nombre del Remitente");

// Establecer la dirección y nombre de (destinatario)

msg.To.Add(new MailAddress("to@domain.com", "Nombre del Destinatario"));

// Establecer cuerpo HTML del mensaje de correo electrónico

msg.HtmlBody = @"<html><p>Este archivo MSG se crea utilizando código C#.</p>" +

	"<p>No es necesario que Microsoft Outlook esté instalado en la máquina que ejecuta este código.</p>" +

	"<p>Este método es adecuado para crear archivos MSG en el lado del servidor.</html>";

// Agregar archivos adjuntos al archivo de mensaje

msg.Attachments.Add(new Attachment("image.bmp"));

msg.Attachments.Add(new Attachment("pic.jpeg"));

// Guardar como archivo MSG de Outlook

string strSaveFile ="TestAspose.msg";

msg.Save(strSaveFile, MessageFormat.Msg);

```
## **Descargar Código de Muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772938)
- [Github](https://github.com/Aspose/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip)
