---
title: "Convertendo Arquivo de Mensagem do Outlook (MSG) para Imagem TIFF"
url: /pt/net/converting-outlook-message-file-msg-to-tiff-image/
weight: 130
type: docs
---


Neste artigo, mostramos como converter um arquivo MSG do Outlook em uma imagem TIFF.

1. Primeiro, leia um arquivo MSG e converta-o para o formato MHTML com Aspose.Email para .NET. Use a classe [Aspose.Email.MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) para carregar o arquivo de mensagem.
1. Após carregar o arquivo, chame o método [MailMessage.Save()](https://apireference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) e salve-o em um fluxo no formato MHTML.
1. Use Aspose.Words para .NET para converter o fluxo MHTML em TIFF. Use a classe [Aspose.Words.Document](https://apireference.aspose.com/net/words/aspose.words/document) para carregar o fluxo MHTML.
1. Por fim, chame o método [Document.Save()](https://apireference.aspose.com/net/words/aspose.words/document/methods/save/index) para salvar o documento MHTML em TIFF.

Se o documento contiver várias páginas, um arquivo TIFF multifacetado será gerado. Os trechos de código abaixo mostram como converter um Arquivo de Mensagem do Outlook (MSG) em Imagem TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}