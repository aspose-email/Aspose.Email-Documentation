---
title: "Análisis de archivos de mensajes de Microsoft Outlook"
url: /es/java/parsing-microsoft-outlook-message-files/
weight: 80
type: docs
---


Con Aspose.Email, puede analizar los mensajes de Microsoft Outlook en unas pocas líneas de código. En este artículo se muestra cómo hacerlo. Aspose.Email tiene clases para realizar muchas tareas de programación con los mensajes de Outlook. El ejemplo de código que aparece a continuación muestra cómo:

1. Carga un mensaje de correo electrónico.
1. Obtén el asunto del correo electrónico.
1. Obtenga el nombre del remitente.
1. Obtenga el cuerpo completo del mensaje.
1. Averigüe si hay archivos adjuntos.
1. Obtenga los nombres de los archivos adjuntos y guárdelos.

El siguiente fragmento de código muestra cómo analizar los archivos de mensajes de Microsoft Outlook.



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