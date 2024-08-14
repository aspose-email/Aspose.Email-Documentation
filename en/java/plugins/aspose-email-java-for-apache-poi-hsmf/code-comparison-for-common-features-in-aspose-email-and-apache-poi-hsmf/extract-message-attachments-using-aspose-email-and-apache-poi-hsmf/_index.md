---
title: Extract Message Attachments using Aspose.Email and Apache POI HSMF
type: docs
weight: 10
url: /java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Extract Message Attachments**
To save attachments from existing messages:

1. Create an instance of the MailMessage class.
1. Load the existing email message using the MailMessage class load() method, specifying the correct MessageFormat.
1. Create an instance of the AttachmentCollection class and fill it with attachments from the MaiMessage instance using the getAttachments() method.
1. Iterate over the AttachmentCollection collection.
1. Create an instance of the Attachment class and fill it with indexed value from the AttachmentCollection using the get() method.
1. Save the attachment to disk using the Attachment class save() method.

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
## **Apache POI HSMF - Extract Message Attachments**
AttachmentChunks class can be used to access attachments of MAPIMessage.

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
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

For more details, visit [Manage Attachments in Email Message](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}
