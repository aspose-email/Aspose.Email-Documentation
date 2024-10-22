---
title: "Extrair Anexos de Mensagens usando Aspose.Email e Apache POI HSMF"
url: /pt/java/extract-message-attachments-using-aspose-email-and-apache-poi-hsmf/
weight: 10
type: docs
---

## **Aspose.Email - Extrair Anexos de Mensagens**
Para salvar anexos de mensagens existentes:

1. Crie uma instância da classe MailMessage.
1. Carregue a mensagem de e-mail existente usando o método load() da classe MailMessage, especificando o formato de mensagem correto.
1. Crie uma instância da classe AttachmentCollection e preencha-a com anexos da instância MailMessage usando o método getAttachments().
1. Percorra a coleção AttachmentCollection.
1. Crie uma instância da classe Attachment e preencha-a com o valor indexado da AttachmentCollection usando o método get().
1. Salve o anexo no disco usando o método save() da classe Attachment.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "message.msg");

System.out.println("Extraindo anexos....");

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Nome do Anexo: " + att.getName());

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    // Salve o anexo no disco

    att.save(dataDir + attFileName);

}

```
## **Apache POI HSMF - Extrair Anexos de Mensagens**
A classe AttachmentChunks pode ser usada para acessar anexos de MAPIMessage.

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
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Gerenciar Anexos em Mensagens de Email](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}