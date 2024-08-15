---
title: "Renderizar hipervínculos con estilo personalizado"
url: /es/net/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---


Puede haber ocasiones en las que necesite generar hipervínculos con un estilo específico según los requisitos de su aplicación. Para eso, Aspose.Email proporciona [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/). Puedes pasar el [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) como parámetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext).

El siguiente fragmento de código muestra cómo usar [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) para generar hipervínculos con su propio estilo personalizado.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}}

Los métodos RenderHyperlinkWithHRef y RenderHyperlinkWithouThRef están diseñados para demostrar la representación de hipervínculos y no están diseñados para su uso en producción.

{{% /alert %}}
