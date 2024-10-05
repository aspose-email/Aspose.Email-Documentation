---
title: Извлечение вложений сообщений с использованием Aspose.Email и Apache POI HSMF
type: docs
weight: 10
url: /java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Извлечение вложений сообщений**
Чтобы сохранить вложения из существующих сообщений:

1. Создайте экземпляр класса MailMessage.
1. Загрузите существующее(email) сообщение с помощью метода load() класса MailMessage, указав правильный формат сообщения.
1. Создайте экземпляр класса AttachmentCollection и заполните его вложениями из экземпляра MaiMessage с помощью метода getAttachments().
1. Переберите коллекцию AttachmentCollection.
1. Создайте экземпляр класса Attachment и заполните его индексированным значением из AttachmentCollection с помощью метода get().
1. Сохраните вложение на диск с помощью метода save() класса Attachment.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "message.msg");

System.out.println("Извлечение вложений....");

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Имя вложения: " + att.getName());

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    // Сохраните вложение на диск

    att.save(dataDir + attFileName);

}

```
## **Apache POI HSMF - Извлечение вложений сообщений**
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
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Для получения дополнительных деталей посетите [Управление вложениями в электронном сообщении](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}