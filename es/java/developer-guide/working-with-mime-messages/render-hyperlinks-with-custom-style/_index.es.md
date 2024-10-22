---
title: "Renderizar hiperenlaces con estilo personalizado"
url: /es/java/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Puede haber momentos en los que necesite generar hiperenlaces con un estilo específico basado en los requisitos de su aplicación. Para ello, Aspose.Email proporciona [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/hyperlinkrenderingcallback/). Puede pasar el **HyperlinkRenderingCallback** como un parámetro de [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText--).

El siguiente fragmento de código le muestra cómo usar **HyperlinkRenderingCallback** para generar hiperenlaces utilizando su propio estilo personalizado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}} 

Los métodos RenderHyperlinkWithHref y RenderHyperlinkWithoutHref están destinados a demostrar la representación de hiperenlaces y no están diseñados para su uso en producción.

{{% /alert %}}