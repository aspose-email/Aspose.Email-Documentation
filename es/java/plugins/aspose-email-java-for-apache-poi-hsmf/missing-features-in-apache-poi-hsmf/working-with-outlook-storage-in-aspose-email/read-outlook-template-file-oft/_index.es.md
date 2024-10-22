---
title: "Leer archivo de plantilla de Outlook OFT"
url: /es/java/read-outlook-template-file-oft/
weight: 40
type: docs
---

## **Aspose.Email - Leer plantilla de Outlook OFT**
La clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) de Aspose.Email se puede utilizar para cargar un archivo de plantilla de Microsoft Outlook (OFT). Una vez que la plantilla de Outlook está cargada en una instancia de la clase MailMessage, puede actualizar el remitente, el destinatario, el cuerpo, el asunto y otras propiedades.

**Java**

``` java

 // Cargar el archivo de plantilla de Outlook (OFT) en la instancia de MailMessage

MailMessage message = MailMessage.load(dataDir + "sample.oft");

// Establecer la información del remitente y de los destinatarios

String senderDisplayName = "John";

String senderEmailAddress = "john@abc.com";

String recipientDisplayName = "William";

String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));

message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));

message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Establecer el nombre, la ubicación y la hora en el cuerpo del correo electrónico

String meetingLocation = "<u>" + "Sala 1, Centro de Convenciones, Nueva York, EE. UU." + "</u>";

String meetingTime = "<u>" + "Lunes, 28 de junio de 2010" + "</u>";

message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));

message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Guardar el mensaje en formato MSG y abrir en Office Outlook

MapiMessage mapimessage = new MapiMessage().fromMailMessage(message);

mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);

mapimessage.save(dataDir + "AsposeInvitation.msg");

```
## **Descargar código en ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Leer archivo de plantilla de Outlook (OFT)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}