---
title: "Analizando Archivos de Mensaje de Microsoft Outlook"
url: /es/java/analizando-archivos-de-mensaje-de-microsoft-outlook/
weight: 80
type: docs
---


Con Aspose.Email, puedes analizar mensajes de Microsoft Outlook en solo unas pocas líneas de código. Este artículo muestra cómo. Aspose.Email tiene clases para realizar muchas tareas de programación con mensajes de Outlook. El siguiente ejemplo de código muestra cómo:

1. Cargar un mensaje de correo electrónico.
1. Obtener el asunto del correo electrónico.
1. Obtener el nombre del remitente.
1. Obtener el cuerpo completo del mensaje.
1. Descubrir si hay archivos adjuntos.
1. Obtener los nombres de los archivos de los archivos adjuntos y guardarlos.

El siguiente fragmento de código muestra cómo analizar archivos de mensajes de Microsoft Outlook.



~~~Java
// The path to the File directory and Load Microsoft Outlook email message file
String dataDir = "data/";
MapiMessage msg = MapiMessage.fromFile(dataDir + "message3.msg");

// Obtain subject of the email message, sender, body and Attachment count
System.out.println("Subject:" + msg.getSubject());
System.out.println("From:" + msg.getSenderName());
System.out.println("Body:" + msg.getBody());
System.out.println("Attachment Count:" + msg.getAttachments().size());

// Iterate through the attachments
for (MapiAttachment attachment : msg.getAttachments()) {
    // Access the attachment's file name and Save attachment
    System.out.println("Attachment:" + attachment.getFileName());
    attachment.save(dataDir + attachment.getLongFileName());
}
~~~