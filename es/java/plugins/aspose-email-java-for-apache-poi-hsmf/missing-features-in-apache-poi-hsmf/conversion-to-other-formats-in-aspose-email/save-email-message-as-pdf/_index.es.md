---
title: "Guardar mensaje de correo electrónico como PDF"
url: /es/java/save-email-message-as-pdf/
weight: 30
type: docs
---

## **Aspose.Email - Guardar mensaje de correo electrónico como PDF**
El siguiente código muestra cómo convertir un mensaje de correo electrónico a PDF utilizando Aspose.Email en combinación con Aspose.Words para Java. Esto implica los siguientes pasos:

1. Cargar el mensaje de correo electrónico usando MailMessage
1. Guardar el mensaje de correo electrónico en MemoryStream como MHTML
1. Cargar el flujo usando Aspose.Words
1. Guardar el mensaje como PDF

**Java**

``` java

 FileInputStream fstream = new FileInputStream(dataDir + "message.msg");

MailMessage eml = MailMessage.load(fstream);

// Guardar el mensaje en el flujo de salida en formato MHTML

ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

eml.save(emlStream, SaveOptions.getDefaultMhtml());

// Cargar el flujo en el documento de Word

LoadOptions lo = new LoadOptions();

lo.setLoadFormat(LoadFormat.MHTML);

Document doc = new Document(new ByteArrayInputStream(

		emlStream.toByteArray()), lo);

// Guardar en disco

doc.save(dataDir + "About Aspose.Pdf", SaveFormat.PDF);

// o guardar en el flujo

ByteArrayOutputStream foStream = new ByteArrayOutputStream();

doc.save(foStream, SaveFormat.PDF);


```
## **Descargar código en funcionamiento**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)

{{% alert color="primary" %}} 

Para más detalles, visite [Guardar un MSG como PDF](/email/java/creating-and-saving-msg-files/).

{{% /alert %}}