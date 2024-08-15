---
title: "Извлеките заголовки сообщений с помощью Aspose.Email и Apache POI HSMF"
url: /ru/java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
weight: 30
type: docs
---

## **Aspose.Email - извлечение заголовков сообщений**
Заголовок электронного письма представляет собой стандартный набор полей заголовков, определенных в Интернете и RFC, включенных в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью класса MailMessage. Общие типы заголовков определены в классе HeaderType. Это запечатанный класс, работающий как обычное перечисление.

**Java**

```java

 //Gets Email Headers

System.out.println("From: " 	+ message.getFrom());

System.out.println("To: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Bcc: " 	+ message.getBcc());

System.out.println("Subject: " 	+ message.getSubject());

```
## **Apache POI HSMF — извлечение заголовков сообщений**
Класс MapiMessage предоставляет методы доступа к заголовкам сообщений электронной почты.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("From: " + msg.getDisplayFrom());

System.out.println("To: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("BCC: " + msg.getDisplayBCC());

System.out.println("Subject: " + msg.getSubject());

```
## **Загрузить рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Извлечение заголовков электронной почты](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}
