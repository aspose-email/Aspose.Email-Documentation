---
title: "Renderizar hiperlinks com estilo personalizado"
url: /pt/java/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Pode haver momentos em que você precise gerar hiperlinks com um estilo específico com base nos requisitos de sua aplicação. Para isso, o Aspose.Email fornece o [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/hyperlinkrenderingcallback/). Você pode passar o **HyperlinkRenderingCallback** como um parâmetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText--). 

O seguinte trecho de código mostra como usar o **HyperlinkRenderingCallback** para gerar hiperlinks usando seu próprio estilo personalizado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}} 

Os métodos RenderHyperlinkWithHref e RenderHyperlinkWithoutHref têm o propósito de demonstrar a renderização de hiperlinks e não são destinados para uso em produção.

{{% /alert %}}