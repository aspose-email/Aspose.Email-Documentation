---
title: "Extraer archivos adjuntos de mensajes usando Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
weight: 10
type: docs
---

## **Aspose.Email - Extraer archivos adjuntos de mensajes**
Para guardar archivos adjuntos de mensajes existentes:

1. Crear una instancia de la clase MailMessage.
1. Cargar el mensaje de correo electrónico existente utilizando el método load() de la clase MailMessage, especificando el formato de mensaje correcto.
1. Crear una instancia de la clase AttachmentCollection y llenarla con los archivos adjuntos de la instancia de MailMessage usando el método getAttachments().
1. Iterar sobre la colección AttachmentCollection.
1. Crear una instancia de la clase Attachment y llenarla con el valor indexado de la AttachmentCollection usando el método get().
1. Guardar el archivo adjunto en el disco utilizando el método save() de la clase Attachment.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "message.msg");

System.out.println("Extrayendo archivos adjuntos....");

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Nombre del archivo adjunto: " + att.getName());

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    // Guardar el archivo adjunto en el disco

    att.save(dataDir + attFileName);

}

```
## **Apache POI HSMF - Extraer archivos adjuntos de mensajes**
La clase AttachmentChunks se puede usar para acceder a los archivos adjuntos de MAPIMessage.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

AttachmentChunks[] attachments = msg.getAttachmentFiles();

if (attachments.length > 0)

{

	File d = new File(dataDir + "attachments");

	if (d.exists() || d.mkdir())

	{

		for (AttachmentChunks attachment : attachments)

		{

			String fileName = attachment.attachFileName.toString();

			if (attachment.attachLongFileName != null)

			{

				fileName = attachment.attachLongFileName.toString();

			}

			File f = new File(d, fileName);

			OutputStream fileOut = null;

			try

			{

				fileOut = new FileOutputStream(f);

				fileOut.write(attachment.attachData.getValue());

			}

			finally

			{

				if (fileOut != null)

				{

					fileOut.close();

				}

			}

		}

	}

}

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para más detalles, visita [Gestionar archivos adjuntos en mensaje de correo electrónico](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}