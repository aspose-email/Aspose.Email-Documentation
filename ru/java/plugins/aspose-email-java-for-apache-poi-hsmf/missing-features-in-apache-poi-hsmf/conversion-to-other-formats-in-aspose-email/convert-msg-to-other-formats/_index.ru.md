---
title: "Конвертируйте MSG в другие форматы"
url: /ru/java/convert-msg-to-other-formats/
weight: 10
type: docs
---

## **Aspose.Email - конвертируйте MSG в другие форматы**
Conversion

**Java**

``` java

 // Initialize and Load an existing MSG file by specifying the MessageFormat

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Save the Email message to disk by specifying the EML and MHT MailMessageSaveType

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email позволяет легко конвертировать сообщения любого типа в другой формат. Чтобы продемонстрировать эту функцию, можно загружать различные типы сообщений с диска и сохранять их в других форматах. Базовый класс SaveOptions и классы EMLSaveOptions, MsgSaveOptions, MhtSaveOptions, HTMLSaveOptions для дополнительных настроек при сохранении MailMessage можно использовать для сохранения сообщений в других форматах. В статье показано, как использовать эти классы для сохранения образца электронного письма в виде:

- [формат EML](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [MSG для Outlook](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [формат MHTML](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [формат HTML](/email/java/loading-and-saving-message/#exporting-email-to-eml).

А также показывает, как сохранить оригинальный адрес электронной почты

- [Сохранить оригинальный адрес электронной почты](/email/java/loading-and-saving-message/)

## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
