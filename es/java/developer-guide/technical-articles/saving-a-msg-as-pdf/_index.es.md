---
title: "Guardar un MSG como PDF"
url: /es/java/saving-a-msg-as-pdf/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Este artículo muestra cómo convertir un mensaje de correo electrónico a PDF con Aspose.Email.
Aspose.Email para Java ofrece las funciones de Microsoft Outlook y no puede gestionar la conversión directa a PDF. Para solucionar este problema, los ejemplos de este artículo utilizan Aspose.Email para convertir el mensaje de correo electrónico en una secuencia MHTML y, a continuación, utilizan Aspose.Words para Java para cargar la secuencia MHTML y, a continuación, guardarla como PDF.

{{% /alert %}} {{% alert color="primary" %}}

Un mensaje de correo electrónico también puede contener archivos adjuntos. Como cada archivo adjunto puede tener un tipo de soporte diferente, Aspose.Email ignora estos archivos adjuntos al convertirlos a MHTML, es decir, solo las imágenes en línea de un mensaje formarán parte de MHTML y se ignorarán los archivos adjuntos normales.

{{% /alert %}}
## **Convertir mensaje de correo electrónico a PDF**
El siguiente código muestra la conversión de un mensaje de correo electrónico a PDF mediante Aspose.Email en combinación con Aspose.Words para Java. Esto implica los siguientes pasos:

1. Cargue el mensaje de correo electrónico con MailMessage
1. Guarde el mensaje de correo electrónico en MemoryStream como MHTML
1. Carga la transmisión con Aspose.Words
1. Guarda el mensaje como PDF

El mensaje de correo electrónico de origen se puede ver de la siguiente manera:

|![todo:image_alt_text](saving-a-msg-as-pdf_1.png)|
|: - |
|**Figura: Archivo MSG de origen** |


|![todo:image_alt_text](saving-a-msg-as-pdf_2.png)|
|: - |
|**Figura: Archivo PDF convertido** |
**Java**

``` java

 static void EmailToPdf(String emailPath) throws Exception

{

       FileInputStream fstream=new FileInputStream(emailPath);

       MailMessage eml = MailMessage.load(fstream);

       //Save the Message to output stream in MHTML format

       ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

       eml.save(emlStream, SaveOptions.getDefaultMhtml());

       //Load the stream in Word document

       LoadOptions lo = new LoadOptions();

       lo.setLoadFormat(LoadFormat.MHTML);

       Document doc = new Document(new ByteArrayInputStream(emlStream.toByteArray()), lo);

       //Save to disc

       doc.save("About Aspose.Pdf", SaveFormat.PDF);

       //or Save to stream

       ByteArrayOutputStream foStream = new ByteArrayOutputStream();

       doc.save(foStream, SaveFormat.PDF);

}

```
