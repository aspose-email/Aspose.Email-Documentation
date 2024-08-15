---
title: "Сохраните сообщение электронной почты с помощью Aspose.Email и Apache POI HSMF"
url: /ru/java/save-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 50
type: docs
---

## **Aspose.Email - Сохранить сообщение электронной почты**
Метод MailMessage.save доступен для сохранения сообщений электронной почты в различных форматах.

**Java**

```java

 MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

messageMSG.save(dataDir + "AsposeMessage.msg");

messageMSG.save(dataDir + "AsposeMessage.eml");

messageMSG.save(dataDir + "AsposeMessage.emlx");

messageMSG.save(dataDir + "AsposeMessage.mht");

```
## **Apache POI HSMF - Сохранить сообщение электронной почты**
Тело электронного письма можно извлечь для создания нового файла.

**Java**

```java

 String filename = "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

PrintWriter txtOut = new PrintWriter("ApacheMessage.txt");

txtOut.println("Email Body: " + msg.getTextBody());

txtOut.close();

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Обновить и сохранить электронное письмо](/email/java/loading-and-saving-message/).

{{% /alert %}}
