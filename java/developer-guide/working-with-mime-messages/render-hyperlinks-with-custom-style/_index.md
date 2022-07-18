---
title: Render Hyperlinks with custom style
type: docs
weight: 70
url: /java/render-hyperlinks-with-custom-style/
---

There may be times when you need to output hyperlinks with some specific style based on the requirements of your application. For that, Aspose.Email provides [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/HyperlinkRenderingCallback). You can pass the [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/HyperlinkRenderingCallback) as a parameter of [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getHtmlBodyText\(com.aspose.email.HyperlinkRenderingCallback\)).

The following code snippet shows you how to use [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/HyperlinkRenderingCallback) to output hyperlinks using your own custom style.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}} 

RenderHyperlinkWithHref and RenderHyperlinkWithoutHref methods are intended to demonstrate hyperlink rendering and are not intended for production use.

{{% /alert %}}
