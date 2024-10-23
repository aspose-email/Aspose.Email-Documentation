---
title: "Salvar Mensagem de Email Como PDF"
url: /pt/java/save-email-message-as-pdf/
weight: 30
type: docs
---

## **Aspose.Email - Salvar Mensagem de Email Como PDF**
O seguinte código mostra como converter uma mensagem de email para PDF usando Aspose.Email em combinação com Aspose.Words para Java. Isso envolve os seguintes passos:

1. Carregar a mensagem de email usando MailMessage
1. Salvar a mensagem de email para MemoryStream como MHTML
1. Carregar o stream usando Aspose.Words
1. Salvar a mensagem como PDF

**Java**

``` java

 FileInputStream fstream = new FileInputStream(dataDir + "message.msg");

MailMessage eml = MailMessage.load(fstream);

// Salvar a Mensagem no stream de saída em formato MHTML

ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

eml.save(emlStream, SaveOptions.getDefaultMhtml());

// Carregar o stream no documento Word

LoadOptions lo = new LoadOptions();

lo.setLoadFormat(LoadFormat.MHTML);

Document doc = new Document(new ByteArrayInputStream(

		emlStream.toByteArray()), lo);

// Salvar no disco

doc.save(dataDir + "About Aspose.Pdf", SaveFormat.PDF);

// ou Salvar no stream

ByteArrayOutputStream foStream = new ByteArrayOutputStream();

doc.save(foStream, SaveFormat.PDF);


```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Salvar Um MSG como PDF](/email/java/creating-and-saving-msg-files/).

{{% /alert %}}