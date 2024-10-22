---
title: "Convertir MSG a Otros Formatos"
url: /es/java/convert-msg-to-other-formats/
weight: 10
type: docs
---

## **Aspose.Email - Convertir MSG a Otros Formatos**
Conversión

**Java**

``` java

 // Inicializar y cargar un archivo MSG existente especificando el MessageFormat

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Guardar el mensaje de correo electrónico en el disco especificando el EML y MHT MailMessageSaveType

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, se pueden cargar diferentes tipos de mensajes desde el disco y guardarlos nuevamente en otros formatos. La clase base SaveOptions y las clases EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions para configuraciones adicionales al guardar MailMessage pueden ser utilizadas para guardar mensajes en otros formatos. El artículo muestra cómo utilizar estas clases para guardar un correo electrónico de ejemplo como:

- [Formato EML](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [Outlook MSG](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [Formato MHTML](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [Formato HTML](/email/java/loading-and-saving-message/#exporting-email-to-eml).

Y también muestra cómo preservar la dirección de correo electrónico original

- [Preservar Dirección de Correo Electrónico Original](/email/java/loading-and-saving-message/)

## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)