---
title: "Creación y almacenamiento de archivos MSG"
url: /es/java/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email admite la creación de archivos de mensajes de Outlook (MSG). En este artículo se explica cómo:

- Crea mensajes MSG.
- Crea mensajes MSG con archivos adjuntos.
- Crea un mensaje MSG con un cuerpo RTF.
- Guarda un mensaje como borrador.
- Trabaja con compresión corporal.
 
## **Creación y almacenamiento de mensajes de Outlook**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) la clase tiene la [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) método que puede guardar archivos MSG de Outlook en un disco o transmisión. Los fragmentos de código que aparecen a continuación crean una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase, establece propiedades como desde, hasta, sujeto y cuerpo. El [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) el método toma el nombre del archivo como argumento. Además, los mensajes de Outlook se pueden crear con un [cuerpo RTF comprimido](#creating-msg-files-with-rtf-body) utilizando el [MapiConversionOptions](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/).

1. Cree una nueva instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clasifica y establece las propiedades Desde, Hasta, Subject y Body.
1. Llame al [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) método que acepta el objeto del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) tipo. El [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) el método convierte el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) en un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) (MSG).
1. Llame al [MapiMessage.save](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) método para guardar el archivo MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Create an instance of the MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);

// Save the message (MSG) file
String strMsgFile = "CreatingAndSavingOutlookMessages_out.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Creación de archivos MSG con archivos adjuntos**

[En el ejemplo anterior](#creating-and-saving-outlook-messages), hemos creado un archivo MSG sencillo. Aspose.Email también permite guardar archivos de mensajes con archivos adjuntos. Todo lo que necesita hacer es agregar los archivos adjuntos al [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia. Añada archivos adjuntos llamando al *addItem* método en el [MailMessage.Attachments](https://reference.aspose.com/email/java/com.aspose.email/attachmentcollection/) collection.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

String[] files = new String[2];
files[0] = "attachment.doc";
files[1] = "attachment.png";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Add the attachments
for (String strFileName : files)
{
    mailMsg.getAttachments().addItem(new Attachment(strFileName));
}

// Create an instance of MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
String strMsgFile = "CreateMessagesWithAttachments.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Creación de archivos MSG con RTF Body**

También puede crear archivos de mensajes de Outlook (MSG) con cuerpos de texto enriquecido (RTF) con Aspose.Email. El cuerpo RTF admite el formato de texto. Cree uno configurando el [MailMessage.HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) propiedad. Cuando conviertes un [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia en un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) por ejemplo, el cuerpo HTML se convierte en RTF. De esta forma, se conserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un formato de encabezado, negrita y subrayado aplicado en el cuerpo del HTML. Este formato se conserva cuando el HTML se convierte a RTF.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setHtmlBody("<h3>rtf example</h3><p>creating an <b><u>outlook message (msg)</u></b> file using Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreatingMSGFilesWithRTFBody_out.msg");
~~~

## **Guardar el mensaje en estado de borrador**

Los correos electrónicos se guardan como borradores cuando alguien ha empezado a editarlos pero quiere volver a ellos para completarlos más tarde. Aspose.Email permite guardar los mensajes de correo electrónico en estado de borrador mediante la configuración de una marca de mensaje. A continuación se muestra un ejemplo de código para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{% alert %}}
Tenga en cuenta que, en el estado de borrador, Outlook no muestra ninguna información del remitente asignada a MapiMessage.
Si necesitamos mostrar la información del remitente, debemos establecer el indicador MSGFLAG_READ.
{{% /alert %}}


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Change properties of an existing MSG file
String strExistingMsg = "message.msg";

// Load the existing file in MailMessage and Change the properties
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " NEW SUBJECT (updated by Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " NEW BODY (udpated by Aspose.Email)");

// Create an instance of type MapiMessage from MailMessage, Set message flag to un-sent (draft status) and Save it
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "SavingMessageInDraftStatus_out.msg");
~~~

## **Implicaciones de la compresión corporal**

El método de compresión corporal RTF se puede utilizar para generar un MSG de menor tamaño. Sin embargo, esto se traduce en una velocidad de creación más lenta. Para crear mensajes con una velocidad mejorada, defina la marca en **false**. Este indicador, a su vez, tiene un efecto en los PST creados: los archivos MSG más pequeños dan como resultado un PST más pequeño, y los archivos MSG grandes hacen que la creación de PST sea más lenta.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~
