---
title: "Renderizar Hiperlinks com Estilo Personalizado"
url: /pt/net/renderizar-hiperlinks-com-estilo-personalizado/
weight: 70
type: docs
---


Pode haver momentos em que você precisa gerar hiperlinks com um estilo específico com base nos requisitos da sua aplicação. Para isso, Aspose.Email fornece [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/). Você pode passar o [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) como um parâmetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext).

O seguinte trecho de código mostra como usar [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) para gerar hiperlinks usando seu próprio estilo personalizado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}} 

Os métodos RenderHyperlinkWithHref e RenderHyperlinkWithoutHref têm a intenção de demonstrar a renderização de hiperlinks e não são destinados ao uso em produção.

{{% /alert %}}