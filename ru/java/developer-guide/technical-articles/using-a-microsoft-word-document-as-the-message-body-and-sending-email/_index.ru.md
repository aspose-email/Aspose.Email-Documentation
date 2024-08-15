---
title: "Использование документа Microsoft Word в качестве текста сообщения и отправка электронной почты"
url: /ru/java/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---


В этой статье показано, как использовать документ Microsoft Word в качестве текста письма и отправлять его получателям. Образец документа представляет собой товарный счет из образца базы данных Northwind, экспортированный в формат Microsoft Word. Aspose.Email для Java занимается сетевыми протоколами и функциями Microsoft Outlook и не может обрабатывать документы Microsoft Word. Чтобы преодолеть эту проблему, в примерах в этой статье используются [Aspose.Слова для Java](https://products.aspose.com/words/java/) чтобы загрузить документ Word и преобразовать его в формат MHTML. Aspose.Email для Java использует документ MHTML в теле письма.
## **Использование документов Microsoft Word в качестве текста письма**
В приведенных ниже примерах программирования показано, как отправить документ Word в виде тела электронного письма с помощью Aspose.Words для Java и Aspose.Email для Java:

1. Загрузите документ Microsoft Word с помощью Aspose.Word для Java [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) class.
1. Сохраните его в формате MHTML.
1. Загрузите документ MHTML с помощью Aspose.Email для Java [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс для установки тела письма.
1. Задайте другие свойства сообщения, используя разные [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) свойства и методы класса.
1. Отправьте электронное письмо с помощью Aspose.Email для Java [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) class.

Исходный документ, счет-фактура продажи, экспортированный в Microsoft Word из образца Microsoft Northwind, можно увидеть ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Когда сообщение отправлено и получено в Microsoft Outlook, оно выглядит так, как показано ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

При просмотре в Outlook или веб-почтовом клиенте, таком как Gmail или Hotmail, форматирование и изображения в формате HTML сохраняются в том же виде, в каком они были в исходном документе. Ниже приведен скриншот сообщения, открываемого в Gmail в браузере Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

В следующем фрагменте кода показано, как использовать документ Microsoft Word в качестве текста сообщения и отправить электронное письмо с помощью [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) экземпляр класса.



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