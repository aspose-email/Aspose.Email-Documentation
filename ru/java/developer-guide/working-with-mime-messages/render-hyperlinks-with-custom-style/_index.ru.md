---
title: "Отображение гиперссылок с пользовательским стилем"
url: /ru/java/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Могут быть случаи, когда вам необходимо выводить гиперссылки с определенным стилем в зависимости от требований вашего приложения. Для этого Aspose.Email предоставляет [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/hyperlinkrenderingcallback/). Вы можете передать **HyperlinkRenderingCallback** в качестве параметра метода [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText--).

Следующий фрагмент кода показывает, как использовать **HyperlinkRenderingCallback** для вывода гиперссылок с использованием вашего собственного пользовательского стиля.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}}

Методы RenderHyperlinkWithHref и RenderHyperlinkWithoutHref предназначены для демонстрации рендеринга гиперссылок и не предназначены для использования в продуктивной среде.

{{% /alert %}}

