---
title: "Guardar un MSG como PDF"
url: /es/java/saving-a-msg-as-pdf/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Este artículo muestra cómo convertir un mensaje de correo electrónico a PDF utilizando Aspose.Email.
Aspose.Email para Java maneja características de Microsoft Outlook y no puede realizar conversiones directas a PDF. Para superar esto, las muestras en este artículo utilizan Aspose.Email para convertir el mensaje de correo electrónico a un flujo MHTML y luego utilizan Aspose.Words para Java para cargar el flujo MHTML y luego guardarlo como PDF.

{{% /alert %}} {{% alert color="primary" %}} 

Un mensaje de correo electrónico también puede contener archivos adjuntos. Dado que cada archivo adjunto puede ser de diferente tipo de medio, Aspose.Email ignora estos archivos adjuntos al convertir a MHTML, es decir, solo las imágenes en línea en un mensaje serán parte de MHTML y cualquier archivo adjunto regular será ignorado.

{{% /alert %}} 
## **Convertir mensaje de correo electrónico a PDF**
El siguiente código muestra cómo convertir un mensaje de correo electrónico a PDF utilizando Aspose.Email en combinación con Aspose.Words para Java. Esto implica los siguientes pasos:

1. Cargar el mensaje de correo electrónico usando MailMessage
1. Guardar el mensaje de correo electrónico en MemoryStream como MHTML
1. Cargar el flujo usando Aspose.Words
1. Guardar el mensaje como PDF

El mensaje de correo electrónico fuente se puede ver como sigue:

|![todo:image_alt_text](saving-a-msg-as-pdf_1.png)|
| :- |
|**Figura: Archivo MSG fuente** |


|![todo:image_alt_text](saving-a-msg-as-pdf_2.png)|
| :- |
|**Figura: Archivo PDF convertido** |
**Java**

``` java

 static void EmailToPdf(String emailPath) throws Exception

{

       FileInputStream fstream=new FileInputStream(emailPath);

       MailMessage eml = MailMessage.load(fstream);

       //Guardar el mensaje en el flujo de salida en formato MHTML

       ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

       eml.save(emlStream, SaveOptions.getDefaultMhtml());

       //Cargar el flujo en el documento de Word

       LoadOptions lo = new LoadOptions();

       lo.setLoadFormat(LoadFormat.MHTML);

       Document doc = new Document(new ByteArrayInputStream(emlStream.toByteArray()), lo);

       //Guardar en disco

       doc.save("About Aspose.Pdf", SaveFormat.PDF);

       //o guardar en el flujo

       ByteArrayOutputStream foStream = new ByteArrayOutputStream();

       doc.save(foStream, SaveFormat.PDF);

}

```