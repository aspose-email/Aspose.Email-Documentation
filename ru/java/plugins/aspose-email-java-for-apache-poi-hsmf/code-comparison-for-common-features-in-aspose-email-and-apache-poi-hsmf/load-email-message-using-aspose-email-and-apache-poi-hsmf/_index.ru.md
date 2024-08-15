---
title: "Загрузите сообщение электронной почты с помощью Aspose.Email и Apache POI HSMF"
url: /ru/java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 40
type: docs
---

## **Aspose.Email - загрузка сообщений электронной почты**
{{% alert color="primary" %}}

The **load** метод, представленный **MailMessage** класс может вызываться разработчиками для загрузки сообщений электронной почты.

{{% /alert %}}

Загрузка различных типов сообщений электронной почты

**Java**

```java

 //Create MailMessage instance by loading an Eml/Msg/Emlx/Mht file

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

```
## **Apache POI HSMF — загрузка сообщений электронной почты**
{{% alert color="primary" %}}

Apache POI HSMF предоставляет конструктор MAPIMessages, который принимает имя файла для загрузки нового MAPIMessage.

{{% /alert %}}

**Java**

```java

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

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
