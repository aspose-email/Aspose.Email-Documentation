---
title: Чтение файла шаблона Outlook OFT
type: docs
weight: 40
url: /java/read-outlook-template-file-oft/
---

## **Aspose.Email - Чтение шаблона Outlook OFT**
Класс Aspose.Email's [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) может быть использован для загрузки файла шаблона Microsoft Outlook (OFT). Как только шаблон Outlook загружен в экземпляр класса MailMessage, вы можете обновить информацию о отправителе, получателе, теле письма, теме и других свойствах.

**Java**

``` java

 // Загрузить файл шаблона Outlook (OFT) в экземпляр MailMessage

MailMessage message = MailMessage.load(dataDir + "sample.oft");

// Установить информацию об отправителе и получателях

String senderDisplayName = "John";

String senderEmailAddress = "john@abc.com";

String recipientDisplayName = "William";

String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));

message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));

message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Установить название, место и время в теле письма

String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";

String meetingTime = "<u>" + "Понедельник, 28 июня 2010" + "</u>";

message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));

message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Сохранить сообщение в формате MSG и открыть в Office Outlook

MapiMessage mapimessage = new MapiMessage().fromMailMessage(message);

mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);

mapimessage.save(dataDir + "AsposeInvitation.msg");

```
## **Скачать рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Чтение файла шаблона Outlook (OFT)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}