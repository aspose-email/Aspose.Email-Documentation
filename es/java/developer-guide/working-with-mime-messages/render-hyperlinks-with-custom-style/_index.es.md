---
title: "Renderizar hipervínculos con un estilo personalizado"
url: /es/java/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Puede haber ocasiones en las que necesite generar hipervínculos con un estilo específico según los requisitos de su aplicación. Para eso, Aspose.Email proporciona [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/hyperlinkrenderingcallback/). Puedes pasar el **HyperlinkRenderingCallback** como parámetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText--).

El siguiente fragmento de código muestra cómo usar **HyperlinkRenderingCallback** para generar hipervínculos con su propio estilo personalizado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}}

Los métodos RenderHyperlinkWithHRef y RenderHyperlinkWithouThRef están diseñados para demostrar la representación de hipervínculos y no están diseñados para su uso en producción.

{{% /alert %}}
