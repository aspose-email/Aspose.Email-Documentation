---
title: "Extraiga los archivos adjuntos de mensajes con Aspose.Email y Apache POI HSMF"
url: /es/java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
weight: 10
type: docs
---

## **Aspose.Email - Extrae los archivos adjuntos de los mensajes**
Para guardar los archivos adjuntos de los mensajes existentes:

1. Crea una instancia de la clase MailMessage.
1. Carga el mensaje de correo electrónico existente con el método load () de la clase MailMessage, especificando el MessageFormat correcto.
1. Crea una instancia de la clase AttachmentCollection y llénala con los datos adjuntos de la instancia de MaiMessage mediante el método getAttachments ().
1. Repasa la colección AttachmentCollection.
1. Crea una instancia de la clase Attachment y llénala con el valor indexado de AttachmentCollection mediante el método get ().
1. Guarde el archivo adjunto en el disco mediante el método save () de la clase Attachment.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "message.msg");

System.out.println("Extracting attachments....");

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Attachment Name: " + att.getName());

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    // Save the attachment to disk

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
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Para obtener más información, visite [Administrar los archivos adjuntos en un mensaje de correo electrónico](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}
