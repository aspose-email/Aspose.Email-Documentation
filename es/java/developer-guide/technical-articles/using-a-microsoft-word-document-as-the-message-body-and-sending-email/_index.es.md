---
title: "Usar un documento de Microsoft Word como el cuerpo del mensaje y enviar correo electrónico"
url: /es/java/usando-un-documento-de-microsoft-word-como-el-cuerpo-del-mensaje-y-enviando-correo-electronico/
weight: 140
type: docs
---


Este artículo te muestra cómo utilizar un documento de Microsoft Word como el cuerpo del correo electrónico y enviarlo a los destinatarios. El documento de ejemplo es una factura de ventas de la base de datos de Northwind, exportada al formato de Microsoft Word. Aspose.Email para Java maneja protocolos de red y características de Microsoft Outlook y no puede gestionar documentos de Microsoft Word. Para superar esto, las muestras en este artículo utilizan [Aspose.Words para Java](https://products.aspose.com/words/java/) para cargar el documento de Word y convertirlo al formato MHTML. Aspose.Email para Java utiliza el documento MHTML en el cuerpo del correo electrónico.
## **Usando documentos de Microsoft Word como cuerpo del correo electrónico**
Los ejemplos de programación a continuación ilustran cómo enviar un documento de Word como cuerpo de un correo electrónico utilizando Aspose.Words para Java y Aspose.Email para Java:

1. Cargar un documento de Microsoft Word utilizando la clase [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) de Aspose.Word para Java.
1. Guardarlo en formato MHTML.
1. Cargar el documento MHTML utilizando la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) de Aspose.Email para Java para establecer el cuerpo del correo electrónico.
1. Establecer otras propiedades del mensaje utilizando diferentes propiedades y métodos de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Enviar el correo electrónico utilizando la clase [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) de Aspose.Email para Java.

El documento de origen, una factura de ventas exportada a Microsoft Word desde el ejemplo de Microsoft Northwind, se puede ver a continuación. 

![todo:image_alt_text](usando-un-documento-de-microsoft-word-como-el-cuerpo-del-mensaje-y-enviando-correo-electronico_1.png)

Cuando el mensaje ha sido enviado y recibido en Microsoft Outlook, se ve como el mensaje a continuación. 

![todo:image_alt_text](usando-un-documento-de-microsoft-word-como-el-cuerpo-del-mensaje-y-enviando-correo-electronico_2.png)

El formato HTML y las imágenes se preservan como en el documento fuente original cuando se ven en Outlook o en un cliente de correo web como Gmail o Hotmail. A continuación se muestra una captura de pantalla del mensaje cuando se abre con Gmail en un navegador Chrome. 

![todo:image_alt_text](usando-un-documento-de-microsoft-word-como-el-cuerpo-del-mensaje-y-enviando-correo-electronico_3.png)

El siguiente fragmento de código muestra cómo usar un documento de Microsoft Word como el cuerpo del mensaje y enviar un correo electrónico utilizando una instancia de la clase [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient).

~~~Java
// La ruta al directorio de archivos
String dataDir = "data/";

// Cargar un documento de Word desde el disco y guardarlo en un flujo como MHTML
Document wordDocument = new Document(dataDir + "Test.doc");
ByteArrayOutputStream mhtmlStream = new ByteArrayOutputStream();
wordDocument.save(mhtmlStream, SaveFormat.MHTML);

// Cargar el MHTML en un objeto MailMessage
MailMessage message = MailMessage.load(new ByteArrayInputStream(mhtmlStream.toByteArray()), new MhtmlLoadOptions());
message.setSubject("Enviando factura en el correo electrónico");
message.setFrom(new MailAddress("sender@gmail.com"));
message.setTo(MailAddressCollection.to_MailAddressCollection("recipient@gmail.com"));

// Guardar el mensaje en formato MSG en el disco
message.save(dataDir + "WordDocAsEmailBody_out.msg", SaveOptions.getDefaultMsgUnicode());

    // Enviar el mensaje de correo electrónico
try (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "pwd")) {
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    client.send(message);
}
~~~