---
title: "Guardar mensaje de correo electrónico como PDF"
url: /es/java/save-email-message-as-pdf/
weight: 30
type: docs
---

## **Aspose.Email: guarda el mensaje de correo electrónico como PDF**
El siguiente código muestra la conversión de un mensaje de correo electrónico a PDF mediante Aspose.Email en combinación con Aspose.Words para Java. Esto implica los siguientes pasos:

1. Cargue el mensaje de correo electrónico con MailMessage
1. Guarde el mensaje de correo electrónico en MemoryStream como MHTML
1. Carga la transmisión con Aspose.Words
1. Guarda el mensaje como PDF

**Java**

``` java

 FileInputStream fstream = new FileInputStream(dataDir + "message.msg");

MailMessage eml = MailMessage.load(fstream);

// Save the Message to output stream in MHTML format

ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

eml.save(emlStream, SaveOptions.getDefaultMhtml());

// Load the stream in Word document

LoadOptions lo = new LoadOptions();

lo.setLoadFormat(LoadFormat.MHTML);

Document doc = new Document(new ByteArrayInputStream(

		emlStream.toByteArray()), lo);

// Save to disc

doc.save(dataDir + "About Aspose.Pdf", SaveFormat.PDF);

// or Save to stream

ByteArrayOutputStream foStream = new ByteArrayOutputStream();

doc.save(foStream, SaveFormat.PDF);


```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Guardar un MSG como PDF](/email/java/creating-and-saving-msg-files/).

{{% /alert %}}
