---
title: "Salvando um Email como PDF"
url: /pt/net/saving-an-email-as-pdf/
weight: 230
type: docs
---


Este artigo mostra como converter uma mensagem de email para PDF usando Aspose.Email. Aspose.Email para .NET lida com protocolos de rede e recursos do Microsoft Outlook, e não pode realizar conversão direta para PDF. Para contornar isso, os exemplos neste artigo usam Aspose.Email para converter a mensagem de email para o stream MHTML e, em seguida, usam Aspose.Words para .NET para carregar o stream MHTML e salvá-lo como PDF. Uma mensagem de email também pode conter anexos. Como cada anexo pode ser de diferentes tipos de mídia, Aspose.Email ignora esses anexos ao converter para MHTML, ou seja, apenas imagens embutidas em uma mensagem serão parte do MHTML e quaisquer anexos regulares serão ignorados.
## **Convertendo Mensagem de Email para PDF**
O código a seguir mostra como converter mensagens de email em PDF usando Aspose.Email em combinação com Aspose.Words para .NET. Isso envolve os seguintes passos:

1. Carregar a mensagem de email usando [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage)
1. Salvar a mensagem de email em MemoryStream como MHTML
1. Carregar o stream usando Aspose.Words
1. Salvar a mensagem como PDF

A mensagem de email de origem pode ser vista da seguinte forma:

![todo:image_alt_text](saving-an-email-as-pdf_1.png)

O PDF convertido é mostrado na seguinte imagem:

![todo:image_alt_text](saving-an-email-as-pdf_2.png)

O seguinte trecho de código mostra como converter mensagens de email para PDF.

```csharp
string dataDir = RunExamples.GetDataDir_KnowledgeBase();
MailMessage mailMsg = MailMessage.Load(dataDir + "message3.msg");
MemoryStream ms = new MemoryStream();
mailMsg.Save(ms, Aspose.Email.SaveOptions.DefaultMhtml);

// create an instance of LoadOptions and set the LoadFormat to Mhtml
var loadOptions = new Aspose.Words.Loading.LoadOptions();
loadOptions.LoadFormat = LoadFormat.Mhtml;

// create an instance of Document and load the MTHML from MemoryStream
var document = new Aspose.Words.Document(ms, loadOptions);

// create an instance of HtmlSaveOptions and set the SaveFormat to Html
var saveOptions = new Aspose.Words.Saving.PdfSaveOptions();
document.Save(dataDir + "SaveEmailAsPDF_out.pdf", saveOptions);
```