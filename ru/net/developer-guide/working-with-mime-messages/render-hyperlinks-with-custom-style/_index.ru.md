---
title: "Рендеринг гиперссылок в пользовательском стиле"
url: /ru/net/render-hyperlinks-with-custom-style/
weight: 70
type: docs
---


Бывают случаи, когда вам нужно выводить гиперссылки в определенном стиле, основанном на требованиях вашего приложения. Для этого Aspose.Email предоставляет [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/). Вы можете сдать экзамен [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) в качестве параметра [MailMessage.GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext).

В следующем фрагменте кода показано, как использовать [HyperlinkRenderingCallback](https://reference.aspose.com/email/net/aspose.email/hyperlinkrenderingcallback/) для вывода гиперссылок с использованием собственного стиля.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-CustomHyperlinkRendering-1.cs" >}}

{{% alert color="primary" %}}

Методы renderHyperlinkWithRef и renderHyperlinkWithRef предназначены для демонстрации рендеринга гиперссылок и не предназначены для производственного использования.

{{% /alert %}}
