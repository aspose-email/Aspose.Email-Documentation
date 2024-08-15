---
title: "Primera aplicación con Aspose.Email Outlook"
url: /es/java/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


En esta sección se muestra cómo usar Aspose.Email Mapi. Creamos una pequeña aplicación que carga un archivo de mensajes de Outlook (TestMessage.msg) y muestra el asunto, las direcciones de origen y destino y el contenido del mensaje. Sigue estos pasos para crear tu primera aplicación con Aspose.Email Outlook.

1. Crea una instancia del [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) clase dando la ruta del archivo de mensajes.
1. Usa las propiedades públicas para mostrar el sujeto, el origen, el destino y el cuerpo.

La implementación de los pasos anteriores se muestra a continuación en el siguiente fragmento de código.



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