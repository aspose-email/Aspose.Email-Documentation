---
title: Render Hyperlinks with Custom Style
type: docs
weight: 70
url: /net/render-hyperlinks-with-custom-style/
---


There may be times when you need to output hyperlinks with some specific style based on the requirements of your application. For that, Aspose.Email provides [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback). You can pass the [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback) as a parameter of [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/gethtmlbodytext).

The following code snippet shows you how to use [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback) to output hyperlinks using your own custom style.



{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}} 

RenderHyperlinkWithHref and RenderHyperlinkWithoutHref methods are intended to demonstrate hyperlink rendering and are not intended for production use.

{{% /alert %}}
