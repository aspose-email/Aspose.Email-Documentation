---
title: "Рендеринг гиперссылок в пользовательском стиле"
url: /ru/java/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---

Бывают случаи, когда вам нужно выводить гиперссылки в определенном стиле, основанном на требованиях вашего приложения. Для этого Aspose.Email предоставляет [HyperlinkRenderingCallback](https://reference.aspose.com/email/java/com.aspose.email/hyperlinkrenderingcallback/). Вы можете сдать экзамен **HyperlinkRenderingCallback** в качестве параметра [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText--).

В следующем фрагменте кода показано, как использовать **HyperlinkRenderingCallback** для вывода гиперссылок с использованием собственного стиля.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CustomHyperlinkRendering-1.java" >}}

{{% alert color="primary" %}}

Методы renderHyperlinkWithRef и renderHyperlinkWithRef предназначены для демонстрации рендеринга гиперссылок и не предназначены для производственного использования.

{{% /alert %}}
