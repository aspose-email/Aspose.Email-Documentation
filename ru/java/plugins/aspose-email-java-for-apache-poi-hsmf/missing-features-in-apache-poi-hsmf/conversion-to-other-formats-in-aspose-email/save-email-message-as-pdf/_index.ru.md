---
title: "Сохранение email сообщения в PDF"
url: /ru/java/save-email-message-as-pdf/
weight: 30
type: docs
---

## **Aspose.Email - Сохранение email сообщения в PDF**
Следующий код демонстрирует, как преобразовать email сообщение в PDF с использованием Aspose.Email в сочетании с Aspose.Words для Java. Это включает в себя следующие шаги:

1. Загрузите email сообщение с помощью MailMessage
1. Сохраните email сообщение в MemoryStream в формате MHTML
1. Загрузите поток с помощью Aspose.Words
1. Сохраните сообщение в формате PDF

**Java**

``` java

 FileInputStream fstream = new FileInputStream(dataDir + "message.msg");

MailMessage eml = MailMessage.load(fstream);

// Сохраните сообщение в выходной поток в формате MHTML

ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

eml.save(emlStream, SaveOptions.getDefaultMhtml());

// Загрузите поток в документ Word

LoadOptions lo = new LoadOptions();

lo.setLoadFormat(LoadFormat.MHTML);

Document doc = new Document(new ByteArrayInputStream(

		emlStream.toByteArray()), lo);

// Сохраните на диск

doc.save(dataDir + "About Aspose.Pdf", SaveFormat.PDF);

// или Сохраните в поток

ByteArrayOutputStream foStream = new ByteArrayOutputStream();

doc.save(foStream, SaveFormat.PDF);


```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/savemessageaspdf/AsposeSaveMessageAsPDF.java)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите [Сохранение MSG в PDF](/email/java/creating-and-saving-msg-files/).

{{% /alert %}}