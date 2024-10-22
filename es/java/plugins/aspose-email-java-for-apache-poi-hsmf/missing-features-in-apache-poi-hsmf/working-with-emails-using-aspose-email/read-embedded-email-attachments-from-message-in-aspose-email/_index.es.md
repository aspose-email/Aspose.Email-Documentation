---
title: "Leer archivos adjuntos de correo electrónico incrustados desde un mensaje en Aspose.Email"
url: /es/java/read-embedded-email-attachments-from-message-in-aspose-email/
weight: 30
type: docs
---

## **Aspose.Email - Leer archivos adjuntos de correo electrónico incrustados desde un mensaje**
A veces, recibimos correos electrónicos con otros correos electrónicos incrustados en ellos como archivos adjuntos. Estos correos electrónicos incrustados son mensajes completos con su propia lista de destinatarios, asunto, cuerpo e incluso archivos adjuntos. Cada uno de estos mensajes también puede contener mensajes incrustados. 
Usando Aspose.Email Java, los desarrolladores pueden acceder a cada mensaje incrustado como un mensaje individual. Este ejemplo muestra cómo utilizar la funcionalidad recursiva.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "embedded.msg", MessageFormat.getMsg());

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Nombre del archivo adjunto: " + att.getName());

    // Obtener el nombre del archivo adjunto. Si el asunto del msg contiene caracteres como :, /, \, etc., reemplazar por espacio

    // porque windows no puede guardar archivos con estos caracteres

    // también guardar los primeros 50 caracteres como nombre de archivo para evitar nombres de archivo largos

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    if (attFileName.length() > 50)

    {

        attFileName = attFileName.substring(0, 50);

    }

    String attExt = (att.getName().substring(att.getName().lastIndexOf("."), att.getName().lastIndexOf(".") + 4));

    // Guardar el archivo adjunto en disco

    att.save(dataPath + attFileName + attExt);

    // Comprobar si es un archivo de texto adjunto huérfano (ATT00001.txt....) y de tipo eml

    if ((attExt.equals(".eml")) || (att.getContentType().getMediaType().equals("text/plain") && att.getName().contains(".txt") == true && att.getName().contains("ATT") == true))

    {

        // Intentar cargar este archivo de texto en MailMessage

        MailMessage attMsg = MailMessage.load(dataPath + attFileName + attExt, MessageFormat.getEml());

        // Llamar a la función recursivamente para analizar este mensaje y los archivos adjuntos

        ParseMessage(attMsg);

    }

}

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Leer archivos adjuntos de correo electrónico incrustados desde un mensaje](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}