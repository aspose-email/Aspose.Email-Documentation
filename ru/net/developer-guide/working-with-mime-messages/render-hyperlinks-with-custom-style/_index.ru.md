---
title: "Отображение гиперссылок с пользовательским стилем"
url: /ru/net/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Могут быть случаи, когда вам нужно вывести гиперссылки с определенным стилем в зависимости от требований вашего приложения. Для этого Aspose.Email предоставляет [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/). Вы можете передать [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) в качестве параметра метода [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext).

Следующий фрагмент кода показывает, как использовать [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) для вывода гиперссылок с использованием вашего собственного пользовательского стиля.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}} 

Методы RenderHyperlinkWithHref и RenderHyperlinkWithoutHref предназначены для демонстрации рендеринга гиперссылок и не предназначены для использования в производственной среде.

{{% /alert %}}