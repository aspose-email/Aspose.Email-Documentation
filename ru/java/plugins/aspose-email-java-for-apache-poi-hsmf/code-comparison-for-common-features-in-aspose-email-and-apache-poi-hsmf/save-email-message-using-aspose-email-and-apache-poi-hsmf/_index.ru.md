---
title: "Сохранение сообщения электронной почты с использованием Aspose.Email и Apache POI HSMF"
url: /ru/java/save-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 50
type: docs
---

## **Aspose.Email - Сохранение сообщения электронной почты**
Метод MailMessage.save доступен для сохранения сообщений электронной почты в различных форматах.

**Java**

```java

 MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

messageMSG.save(dataDir + "AsposeMessage.msg");

messageMSG.save(dataDir + "AsposeMessage.eml");

messageMSG.save(dataDir + "AsposeMessage.emlx");

messageMSG.save(dataDir + "AsposeMessage.mht");

```
## **Apache POI HSMF - Сохранение сообщения электронной почты**
Тело электронной почты можно извлечь для создания нового файла.

**Java**

```java

 String filename = "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

PrintWriter txtOut = new PrintWriter("ApacheMessage.txt");

txtOut.println("Тело письма: " + msg.getTextBody());

txtOut.close();

```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите [Обновление и сохранение электронной почты](/email/java/loading-and-saving-message/).

{{% /alert %}}