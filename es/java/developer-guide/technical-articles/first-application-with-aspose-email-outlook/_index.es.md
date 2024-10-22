---
title: "Primera aplicación con Aspose.Email Outlook"
url: /es/java/primera-aplicacion-con-aspose-email-outlook/
weight: 280
type: docs
---


Esta sección demuestra cómo usar Aspose.Email Mapi. Creamos una pequeña aplicación que carga un archivo de mensaje de Outlook (TestMessage.msg) y muestra el asunto, las direcciones de correo del remitente y del destinatario, y el contenido del cuerpo. Siga estos pasos para crear su primera aplicación utilizando Aspose.Email Outlook.

1. Cree una instancia de la clase [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) proporcionando la ruta del archivo de mensaje.
1. Utilice las propiedades públicas para mostrar el asunto, de, para y cuerpo.

La implementación de los pasos anteriores se demuestra a continuación en el siguiente fragmento de código.



~~~Java
// Load the outlook message file
MapiMessage msg = MapiMessage.fromFile("outlookmessage.msg");

// Use the public properties
//read subject
System.out.print("Subject:" + msg.getSubject());

//sender name
System.out.print("From:" + msg.getSenderName());

//message body
System.out.print("Body:" + msg.getBody());

//Attachments
for(MapiAttachment att : msg.getAttachments())
{
    System.out.print("Attachment Name:"+att.getFileName());
    att.save(att.getFileName());
}
~~~