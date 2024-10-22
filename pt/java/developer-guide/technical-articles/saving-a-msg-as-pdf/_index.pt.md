---
title: "Salvando um MSG como PDF"
url: /pt/java/saving-a-msg-as-pdf/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Este artigo mostra como converter uma mensagem de email em PDF usando Aspose.Email.
Aspose.Email para Java lida com recursos do Microsoft Outlook e não pode fazer conversão direta para PDF. Para contornar isso, os exemplos neste artigo usam Aspose.Email para converter a mensagem de email em um fluxo MHTML e, em seguida, usam Aspose.Words para Java para carregar o fluxo MHTML e, em seguida, salvá-lo como PDF.

{{% /alert %}} {{% alert color="primary" %}} 

Uma mensagem de email também pode conter anexos. Como cada anexo pode ser de um tipo de mídia diferente, o Aspose.Email ignora esses anexos ao converter para MHTML, ou seja, apenas imagens inline em uma mensagem farão parte do MHTML e qualquer anexo regular será ignorado.

{{% /alert %}} 
## **Converter mensagem de email para PDF**
O código a seguir mostra a conversão de uma mensagem de email para PDF usando Aspose.Email em combinação com Aspose.Words para Java. Isso envolve os seguintes passos:

1. Carregar a mensagem de email usando MailMessage
1. Salvar a mensagem de email em MemoryStream como MHTML
1. Carregar o fluxo usando Aspose.Words
1. Salvar a mensagem como PDF

A mensagem de email de origem pode ser vista da seguinte forma:

|![todo:image_alt_text](saving-a-msg-as-pdf_1.png)|
| :- |
|**Figura: Arquivo MSG de Origem** |


|![todo:image_alt_text](saving-a-msg-as-pdf_2.png)|
| :- |
|**Figura: Arquivo PDF Convertido** |
**Java**

``` java

 static void EmailToPdf(String emailPath) throws Exception

{

       FileInputStream fstream=new FileInputStream(emailPath);

       MailMessage eml = MailMessage.load(fstream);

       //Salvar a Mensagem no fluxo de saída em formato MHTML

       ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

       eml.save(emlStream, SaveOptions.getDefaultMhtml());

       //Carregar o fluxo no documento do Word

       LoadOptions lo = new LoadOptions();

       lo.setLoadFormat(LoadFormat.MHTML);

       Document doc = new Document(new ByteArrayInputStream(emlStream.toByteArray()), lo);

       //Salvar no disco

       doc.save("About Aspose.Pdf", SaveFormat.PDF);

       //ou salvar no fluxo

       ByteArrayOutputStream foStream = new ByteArrayOutputStream();

       doc.save(foStream, SaveFormat.PDF);

}

```