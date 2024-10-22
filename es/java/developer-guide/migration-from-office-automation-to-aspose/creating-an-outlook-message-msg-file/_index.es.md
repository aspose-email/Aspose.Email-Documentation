---
title: "Creando un Archivo de Mensaje de Outlook (MSG)"
url: /es/java/creando-un-archivo-de-mensaje-de-outlook-msg/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Nuestros consejos de migración muestran cómo los productos Aspose pueden ser utilizados para mejorar tus aplicaciones y liberarte de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo crear un archivo de mensaje de Outlook (MSG) utilizando [Microsoft Office Automation](#office-automation) y [Aspose.Email](#asposeemail-for-java). Las muestras de código establecen las propiedades básicas del archivo MSG - Para, Cc, Asunto y cuerpo HTML - antes de guardar el archivo en el disco.

{{% /alert %}} 
## **Automatización de Office**
Para usar la Automatización de Office, Microsoft Outlook debe estar instalado en la máquina donde se ejecuta el código. También se requiere una referencia a Outlook.interop.dll.
### **Muestras de Programación**
Las siguientes muestras de código crean un archivo MSG utilizando la Automatización de Office.

**C#**

~~~cs

 // Crea una nueva instancia de la Aplicación de Outlook

Outlook.Application objOutlook = new Outlook.Application();

// Creando un nuevo mensaje de Outlook desde la instancia de la Aplicación de Outlook

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Establecer la información del destinatario

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Establecer el asunto del mensaje

msgInterop.Subject = "Asunto";

// Establecer un texto HTML en el cuerpo HTML

msgInterop.HTMLBody = "<h3>Encabezado HTML 3</h3> <u>Este es un texto subrayado</u>";

// Guardar el archivo MSG en el disco local

string strMsg = @"c:\\temp\TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);



~~~
## **Aspose.Email para Java**
Las muestras a continuación utilizan Aspose.Email para crear el archivo MSG de Outlook. Está escrito en Java puro y no utiliza COM Interop. No se requiere la instalación de Outlook para crear el archivo msg de esta manera.

~~~Java

// Crear una instancia de la clase Aspose.Email.MailMessage
MailMessage msg = new MailMessage();

// Establecer la información de los destinatarios
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setCC(MailAddressCollection.to_MailAddressCollection("cc@domain.com"));

// Establecer el asunto
msg.setSubject("Asunto");

// Establecer el cuerpo HTML
msg.setHtmlBody("<h3>Encabezado HTML 3</h3> <u>Este es un texto subrayado</u>");

// Agregar un archivo adjunto
msg.getAttachments().addItem(new Attachment("test.txt"));

// Guardarlo en el disco local
String strMsg = "c:\\ TestAspose.msg";
msg.save(strMsg, SaveOptions.getDefaultMsgUnicode());

~~~