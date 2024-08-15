---
title: "Convertir MSG a otros formatos"
url: /es/java/convert-msg-to-other-formats/
weight: 10
type: docs
---

## **Aspose.Email - Convertir MSG a otros formatos**
Conversion

**Java**

``` java

 // Initialize and Load an existing MSG file by specifying the MessageFormat

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Save the Email message to disk by specifying the EML and MHT MailMessageSaveType

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, se pueden cargar diferentes tipos de mensajes desde el disco y guardarlos en otros formatos. La clase base SaveOptions y las clases EMLSaveOptions, MsgSaveOptions, MhtSaveOptions, HtSaveOptions y HTMLSaveOptions ofrecen opciones adicionales a la hora de guardar MailMessage y se pueden usar para guardar mensajes en otros formatos. En el artículo se muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- [Formato EML](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [MSG de Outlook](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [Formato MHTML](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [Formato HTML](/email/java/loading-and-saving-message/#exporting-email-to-eml).

Y también muestra cómo conservar la dirección de correo electrónico original

- [Conservar la dirección de correo electrónico original](/email/java/loading-and-saving-message/)

## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
