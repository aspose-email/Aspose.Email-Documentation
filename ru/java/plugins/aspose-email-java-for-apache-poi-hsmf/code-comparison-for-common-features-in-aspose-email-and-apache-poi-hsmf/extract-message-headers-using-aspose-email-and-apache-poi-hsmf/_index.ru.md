---
title: "Извлечение заголовков сообщений с использованием Aspose.Email и Apache POI HSMF"
url: /ru/java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
weight: 30
type: docs
---

## **Aspose.Email - Извлечение заголовков сообщений**
Заголовок электронной почты представляет собой стандартный набор полей заголовков, определенный в интернете и RFC, включенных в интернет-сообщения электронной почты. Заголовок электронной почты можно указать с помощью класса MailMessage. Общие типы заголовков определены в классе HeaderType. Это закрытый класс, работающий как обычная перечисляемая величина.

**Java**

```java

 //Gets Email Headers

System.out.println("From: " 	+ message.getFrom());

System.out.println("To: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Bcc: " 	+ message.getBcc());

System.out.println("Subject: " 	+ message.getSubject());

```
## **Apache POI HSMF - Извлечение заголовков сообщений**
Класс MAPIMessage предоставляет методы для доступа к заголовкам электронных писем.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("From: " + msg.getDisplayFrom());

System.out.println("To: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("BCC: " + msg.getDisplayBCC());

System.out.println("Subject: " + msg.getSubject());

```
## **Скачать рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Извлечение заголовков электронной почты](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}