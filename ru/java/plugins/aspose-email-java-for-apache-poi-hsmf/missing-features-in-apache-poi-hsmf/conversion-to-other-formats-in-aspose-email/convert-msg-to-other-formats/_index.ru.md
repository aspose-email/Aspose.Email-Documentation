---
title: "Конвертировать MSG в другие форматы"
url: /ru/java/convert-msg-to-other-formats/
weight: 10
type: docs
---

## **Aspose.Email - Конвертировать MSG в другие форматы**
Конвертация

**Java**

``` java

 // Инициализируйте и загрузите существующий MSG файл, указав формат сообщения

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Сохраните электронное сообщение на диск, указав EML и MHT MailMessageSaveType

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email упрощает конвертацию любого типа сообщения в другой формат. Чтобы продемонстрировать эту функцию, различные типы сообщений могут быть загружены с диска и сохранены обратно в других форматах. Базовый класс SaveOptions и классы EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions для дополнительных настроек при сохранении MailMessage могут быть использованы для сохранения сообщений в другие форматы. В статье показано, как использовать эти классы для сохранения примера электронного письма в формате:

- [EML формат](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [Outlook MSG](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [MHTML формат](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [HTML формат](/email/java/loading-and-saving-message/#exporting-email-to-eml).

А также показано, как сохранить оригинальный адрес электронной почты

- [Сохранить оригинальный адрес электронной почты](/email/java/loading-and-saving-message/)

## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)