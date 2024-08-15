---
title: "Uso de un documento de Microsoft Word como cuerpo del mensaje y envío de correo electrónico"
url: /es/java/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---


En este artículo se muestra cómo usar un documento de Microsoft Word como cuerpo del correo electrónico y enviarlo a los destinatarios. El documento de muestra es una factura de venta de la muestra de la base de datos Northwind, exportada al formato Microsoft Word. Aspose.Email para Java utiliza los protocolos de red y las funciones de Microsoft Outlook y no puede gestionar documentos de Microsoft Word. Para superar esto, los ejemplos de este artículo utilizan [Aspose.Words para Java](https://products.aspose.com/words/java/) para cargar el documento de Word y convertirlo a formato MHTML. Aspose.Email para Java usa el documento MHTML en el cuerpo del correo electrónico.
## **Uso de documentos de Microsoft Word como cuerpo de correo electrónico**
Los siguientes ejemplos de programación muestran cómo enviar un documento de Word como cuerpo de correo electrónico mediante Aspose.Words para Java y Aspose.Email para Java:

1. Cargue un documento de Microsoft Word usando Aspose.Word para Java [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) class.
1. Guárdalo en formato MHTML.
1. Cargue el documento MHTML usando Aspose.Email para Java [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase para configurar el cuerpo del correo electrónico.
1. Establezca otras propiedades del mensaje utilizando diferentes [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) propiedades y métodos de clase.
1. Envíe el correo electrónico usando Aspose.Email para Java [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) class.

El documento fuente, una factura de venta exportada a Microsoft Word desde la muestra de Microsoft Northwind, se puede ver a continuación.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Cuando el mensaje se haya enviado y recibido en Microsoft Outlook, tendrá el mismo aspecto que el siguiente mensaje.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

El formato HTML y las imágenes se conservan como en el documento original cuando se ven en Outlook o en un cliente de correo electrónico web como Gmail o Hotmail. A continuación se muestra una captura de pantalla del mensaje cuando se abre con Gmail en un navegador Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

El siguiente fragmento de código muestra cómo usar un documento de Microsoft Word como cuerpo del mensaje y enviar un correo electrónico mediante [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) instancia de clase.



~~~Java
// The path to the File directory
String dataDir = "data/";

// Load a Word document from disk and save it to stream as MHTML
Document wordDocument = new Document(dataDir + "Test.doc");
ByteArrayOutputStream mhtmlStream = new ByteArrayOutputStream();
wordDocument.save(mhtmlStream, SaveFormat.MHTML);

// Load the MHTML in a MailMessage object
MailMessage message = MailMessage.load(new ByteArrayInputStream(mhtmlStream.toByteArray()), new MhtmlLoadOptions());
message.setSubject("Sending Invoice in Email");
message.setFrom(new MailAddress("sender@gmail.com"));
message.setTo(MailAddressCollection.to_MailAddressCollection("recipient@gmail.com"));

// Save the message in MSG format to disk
message.save(dataDir + "WordDocAsEmailBody_out.msg", SaveOptions.getDefaultMsgUnicode());

    // Send the email message
try (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "pwd")) {
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    client.send(message);
}
~~~