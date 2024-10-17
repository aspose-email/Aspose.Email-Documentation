---
title: "Agregar Imágenes Incrustadas a Mensajes de Correo en Aspose.Email"
url: /es/java/add-embedded-images-to-email-message-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Agregar Imágenes Incrustadas a Mensajes de Correo**
Con Aspose.Email, los desarrolladores de Java pueden incrustar fácilmente cualquier imagen en un mensaje de correo, así como adjuntarla, como se discute en [Gestionar Archivos Adjuntos en Mensajes de Correo](/email/java/working-with-message-attachments). Para incrustar una imagen, Aspose.Email utiliza una clase especializada, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Establecer cuerpo Html. También contiene una etiqueta <img> con cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>"

        + "<font color=blue>Esta línea está en color azul</font><br><br>" +

        "Aquí hay una imagen incrustada.<img src=cid:companylogo>");

// Agregar recurso vinculado

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Agregar recurso vinculado a la colección de recursos vinculados del mensaje

message.getLinkedResources().addItem(res);

```
## **Descargar Código en Ejecución**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Agregar Imágenes Incrustadas a Mensajes de Correo](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}