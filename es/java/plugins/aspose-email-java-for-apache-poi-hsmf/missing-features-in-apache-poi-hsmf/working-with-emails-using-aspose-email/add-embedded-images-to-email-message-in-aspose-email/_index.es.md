---
title: "Agregar imágenes incrustadas al mensaje de correo electrónico en Aspose.Email"
url: /es/java/add-embedded-images-to-email-message-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Agregar imágenes incrustadas a un mensaje de correo electrónico**
Con Aspose.Email, los desarrolladores de Java pueden incrustar fácilmente cualquier imagen en un mensaje de correo electrónico y adjuntarla, tal y como se explica en [Administrar los archivos adjuntos en un mensaje de correo electrónico](/email/java/working-with-message-attachments). Para incrustar una imagen, Aspose.Email usa una clase especializada, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Set Html body. It also contains <img> tag with cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>"

        + "<font color=blue>This line is in blue color</font><br><br>" +

        "Here is an embedded image.<img src=cid:companylogo>");

// Add linked resource

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Add Linked resource to the message's Linked resource collection

message.getLinkedResources().addItem(res);

```
## **Descargar Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Agregar imágenes incrustadas al mensaje de correo electrónico](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}
