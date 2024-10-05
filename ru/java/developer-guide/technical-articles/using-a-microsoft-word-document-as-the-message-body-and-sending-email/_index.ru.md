---
title: "Использование документа Microsoft Word в качестве тела сообщения и отправка электронной почты"
url: /ru/java/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---

Эта статья показывает, как использовать документ Microsoft Word в качестве тела электронной почты и отправить его получателям. Пример документа — это счет-фактура из базы данных Northwind, экспортированный в формат Microsoft Word. Aspose.Email для Java работает с сетевыми протоколами и функциями Microsoft Outlook и не может обрабатывать документы Microsoft Word. Чтобы преодолеть это, примеры в этой статье используют [Aspose.Words для Java](https://products.aspose.com/words/java/) для загрузки документа Word и преобразования его в формат MHTML. Aspose.Email для Java использует документ MHTML в теле электронного письма.
## **Использование документов Microsoft Word в качестве тела электронной почты**
Программистские примеры ниже иллюстрируют, как отправить документ Word в качестве тела электронной почты, используя Aspose.Words для Java и Aspose.Email для Java:

1. Загрузите документ Microsoft Word с помощью класса [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) из Aspose.Word для Java.
1. Сохраните его в формате MHTML.
1. Загрузите документ MHTML с помощью класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) из Aspose.Email для Java, чтобы установить тело электронной почты.
1. Установите другие свойства сообщения с помощью различных свойств и методов класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Отправьте электронное письмо с использованием класса [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) из Aspose.Email для Java.

Исходный документ, счет-фактура, экспортированный в Microsoft Word из примера Microsoft Northwind, можно увидеть ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Когда сообщение было отправлено и получено в Microsoft Outlook, оно выглядит как сообщение ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

HTML-форматирование и изображения сохраняются, как в исходном документе, при просмотре как в Outlook, так и в веб-клиенте электронной почты, таком как Gmail или Hotmail. Ниже приведен скриншот сообщения, открытого с помощью Gmail в браузере Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

Следующий фрагмент кода показывает, как использовать документ Microsoft Word в качестве тела сообщения и отправить электронное письмо, используя экземпляр класса [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient).

~~~Java
// The path to the File directory
String dataDir = "data/";

// Load a Word document from disk and save it to stream as MHTML
Document wordDocument = new Document(dataDir + "Test.doc");
ByteArrayOutputStream mhtmlStream = new ByteArrayOutputStream();
wordDocument.save(mhtmlStream, SaveFormat.MHTML);

// Load the MHTML in a MailMessage object
MailMessage message = MailMessage.load(new ByteArrayInputStream(mhtmlStream.toByteArray()), new MhtmlLoadOptions());
message.setSubject("Sending Invoice in Email");
message.setFrom(new MailAddress("sender@gmail.com"));
message.setTo(MailAddressCollection.to_MailAddressCollection("recipient@gmail.com"));

// Save the message in MSG format to disk
message.save(dataDir + "WordDocAsEmailBody_out.msg", SaveOptions.getDefaultMsgUnicode());

    // Send the email message
try (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "pwd")) {
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    client.send(message);
}
~~~