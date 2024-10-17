---
title: "Renderizar hiperenlaces con estilo personalizado"
url: /es/net/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Puede haber momentos en los que necesite mostrar hiperenlaces con un estilo específico basado en los requisitos de su aplicación. Para eso, Aspose.Email proporciona [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/). Puede pasar el [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) como un parámetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext).

El siguiente fragmento de código le muestra cómo usar [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) para mostrar hiperenlaces utilizando su propio estilo personalizado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}} 

Los métodos RenderHyperlinkWithHref y RenderHyperlinkWithoutHref están destinados a demostrar la renderización de hiperenlaces y no están destinados para uso en producción.

{{% /alert %}}