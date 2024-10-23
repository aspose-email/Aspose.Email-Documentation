---
title: "Ler Anexos de Email Incorporados de Mensagens no Aspose.Email"
url: /pt/java/read-embedded-email-attachments-from-message-in-aspose-email/
weight: 30
type: docs
---

## **Aspose.Email - Ler Anexos de Email Incorporados de Mensagens**
Às vezes, recebemos e-mails com outros e-mails incorporados a eles como anexos. Esses e-mails incorporados são mensagens completas com sua própria lista de destinatários, assunto, corpo e até mesmo anexos. Cada uma dessas mensagens também pode conter mensagens incorporadas.
Usando o Aspose.Email Java, os desenvolvedores podem acessar cada mensagem incorporada como uma mensagem individual. Este exemplo mostra como usar a funcionalidade recursiva.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "embedded.msg", MessageFormat.getMsg());

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Nome do Anexo: " + att.getName());

    // Obter o nome do anexo. Se o assunto do msg contiver caracteres como :, /, \ etc., substitua por espaço

    // porque o windows não pode salvar arquivos com esses caracteres

    // também salve os primeiros 50 caracteres como nome de arquivo para evitar nomes de arquivos longos

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    if (attFileName.length() > 50)

    {

        attFileName = attFileName.substring(0, 50);

    }

    String attExt = (att.getName().substring(att.getName().lastIndexOf("."), att.getName().lastIndexOf(".") + 4));

    // Salvar o anexo no disco

    att.save(dataPath + attFileName + attExt);

    // Verificar se é um arquivo de anexo de texto órfão (ATT00001.txt....) e do tipo eml

    if ((attExt.equals(".eml")) || (att.getContentType().getMediaType().equals("text/plain") && att.getName().contains(".txt") == true && att.getName().contains("ATT") == true))

    {

        // Tentar carregar este arquivo de texto em MailMessage

        MailMessage attMsg = MailMessage.load(dataPath + attFileName + attExt, MessageFormat.getEml());

        // Chamar a função recursivamente para analisar esta mensagem e anexos

        ParseMessage(attMsg);

    }

}

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Ler Anexos de Email Incorporados de Mensagens](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}