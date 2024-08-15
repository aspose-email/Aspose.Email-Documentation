---
title: "Извлеките текст сообщения с помощью Aspose.Email и Apache POI HSMF"
url: /ru/java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/
weight: 20
type: docs
---

## **Aspose.Email - извлечение текста сообщения**
MailMessage представляет собой сообщение электронной почты и позволяет разработчикам получать доступ к свойствам сообщения электронной почты. Информация в заголовке (обсуждается в [Извлечение заголовков электронной почты](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) можно извлекать и манипулировать им по-разному.

**Java**

```java

 MailMessage msg = MailMessage.load(dataDir + "message.msg");

System.out.println("Body:"+ msg.getBody());

System.out.println("Text Body:"+ msg.getTextBody());

System.out.println("Text Body HTML:"+ msg.getHtmlBody());

```
## **Apache POI HSMF — извлечение текста сообщения**
MapiMessage может получить доступ к телу сообщения электронной почты.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("Text Body:"+ msg.getTextBody());

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Отображение информации об электронной почте на экране](/email/java/display-information-in-custom-order-in-mhtml-files/).

{{% /alert %}}
