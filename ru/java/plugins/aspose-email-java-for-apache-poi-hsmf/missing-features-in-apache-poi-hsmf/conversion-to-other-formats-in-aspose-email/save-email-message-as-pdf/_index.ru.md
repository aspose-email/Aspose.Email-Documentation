---
title: "Сохранить сообщение электронной почты в формате PDF"
url: /ru/java/save-email-message-as-pdf/
weight: 30
type: docs
---

## **Aspose.Email - Сохранить сообщение электронной почты в формате PDF**
Следующий код показывает преобразование сообщения электронной почты в PDF с помощью Aspose.Email в сочетании с Aspose.Words для Java. Это включает в себя следующие шаги:

1. Загрузите сообщение электронной почты с помощью MailMessage
1. Сохраните сообщение электронной почты в MemoryStream в формате MHTML
1. Загрузите трансляцию с помощью Aspose.Words
1. Сохранить сообщение в формате PDF

**Java**

``` java

 FileInputStream fstream = new FileInputStream(dataDir + "message.msg");

MailMessage eml = MailMessage.load(fstream);

// Save the Message to output stream in MHTML format

ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

eml.save(emlStream, SaveOptions.getDefaultMhtml());

// Load the stream in Word document

LoadOptions lo = new LoadOptions();

lo.setLoadFormat(LoadFormat.MHTML);

Document doc = new Document(new ByteArrayInputStream(

		emlStream.toByteArray()), lo);

// Save to disc

doc.save(dataDir + "About Aspose.Pdf", SaveFormat.PDF);

// or Save to stream

ByteArrayOutputStream foStream = new ByteArrayOutputStream();

doc.save(foStream, SaveFormat.PDF);


```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Сохранение файла MSG в формате PDF](/email/java/creating-and-saving-msg-files/).

{{% /alert %}}
