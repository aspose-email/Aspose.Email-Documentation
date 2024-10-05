---
title: Загрузка электронного сообщения с помощью Aspose.Email и Apache POI HSMF
type: docs
weight: 40
url: /java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Загрузка электронных сообщений**
{{% alert color="primary" %}} 

Метод **load**, предоставляемый классом **MailMessage**, может быть вызван разработчиками для загрузки электронных сообщений.

{{% /alert %}} 

Загрузка различных типов электронных сообщений

**Java**

```java

 //Создание экземпляра MailMessage путем загрузки файла Eml/Msg/Emlx/Mht

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

```
## **Apache POI HSMF - Загрузка электронных сообщений**
{{% alert color="primary" %}} 

Apache POI HSMF предоставляет конструктор MAPIMessages, который принимает имя файла для загрузки нового MAPIMessage.

{{% /alert %}} 

**Java**

```java

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

```
## **Скачать рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Обновление и сохранение электронного письма](/email/java/loading-and-saving-message/).

{{% /alert %}}