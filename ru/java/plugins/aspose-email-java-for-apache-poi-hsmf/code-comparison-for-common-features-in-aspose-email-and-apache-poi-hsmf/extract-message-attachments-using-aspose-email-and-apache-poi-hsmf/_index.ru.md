---
title: "Извлекайте вложения сообщений с помощью Aspose.Email и Apache POI HSMF"
url: /ru/java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
weight: 10
type: docs
---

## **Aspose.Email - Извлечение вложений сообщений**
Чтобы сохранить вложения из существующих сообщений, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
1. Загрузите существующее сообщение электронной почты с помощью метода load () класса MailMessage, указав правильный формат MessageFormat.
1. Создайте экземпляр класса AttachmentCollection и заполните его вложениями из экземпляра MaiMessage с помощью метода getAttachments ().
1. Проведите итерацию по коллекции AttachmentCollection.
1. Создайте экземпляр класса Attachment и заполните его индексированным значением из AttachmentCollection с помощью метода get ().
1. Сохраните вложение на диск, используя метод save () класса Attachment.

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
## **Apache POI HSMF — извлечение вложений сообщений**
Класс AttachmentChunks можно использовать для доступа к вложениям MAPIMessage.

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
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Управление вложениями в сообщении электронной почты](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}
