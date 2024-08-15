---
title: "Использование документа Microsoft Word в качестве текста сообщения и отправка электронной почты"
url: /ru/net/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---


В этой статье показано, как использовать документ Microsoft Word в качестве текста письма и отправлять его получателям. Образец документа представляет собой товарный счет из образца базы данных Northwind, экспортированный в формат Microsoft Word. Aspose.Email for .NET занимается сетевыми протоколами и функциями Microsoft Outlook и не может обрабатывать документы Microsoft Word. Чтобы преодолеть эту проблему, в примерах в этой статье используются [Aspose.Слова для .NET](https://products.aspose.com/words/net/) чтобы загрузить документ Word и преобразовать его в формат MHTML. Aspose.Email для .NET использует документ MHTML в теле письма.
## **Использование документов Microsoft Word в качестве текста письма**
В приведенных ниже примерах программирования показано, как отправить документ Word в виде тела электронного письма с помощью Aspose.Words для .NET и Aspose.Email для .NET:

1. Загрузите документ Microsoft Word, используя Aspose.Word для файлов.NET [Document](https://apireference.aspose.com/words/net/aspose.words/document) class.
1. Сохраните его в формате MHTML.
1. Загрузите документ MHTML с помощью Aspose.Email для файлов.NET [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) класс для установки тела письма.
1. Задайте другие свойства сообщения, используя разные [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) свойства и методы класса.
1. Отправьте электронное письмо с помощью Aspose.Email для .NET [SMTPClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) class.

Исходный документ, счет-фактура продажи, экспортированный в Microsoft Word из образца Microsoft Northwind, можно увидеть ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Когда сообщение отправлено и получено в Microsoft Outlook, оно выглядит так, как показано ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

При просмотре в Outlook или веб-почтовом клиенте, таком как Gmail или Hotmail, форматирование и изображения в формате HTML сохраняются в том же виде, в каком они были в исходном документе. Ниже приведен скриншот сообщения, открываемого в Gmail в браузере Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

В следующем фрагменте кода показано, как использовать документ Microsoft Word в качестве текста сообщения и отправить электронное письмо с помощью [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) экземпляр класса.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Load a Word document from disk and save it to stream as MHTML
Document wordDocument = new Document(folderPath + "invoice.docx");
MemoryStream mhtmlStream = new MemoryStream();
wordDocument.Save(mhtmlStream, SaveFormat.Mhtml);

// Load the MHTML in a MailMessage object
mhtmlStream.Position = 0;
using (MailMessage message = MailMessage.Load(mhtmlStream, new MhtmlLoadOptions()))
{
    message.Subject = "Sending Invoice by Email";
    message.From = "sender@gmail.com";
    message.To = "recipient@gmail.com";

    // Save the message in MSG format to disk
    message.Save(folderPath + "WordDocAsEmailBody_out.msg", SaveOptions.DefaultMsgUnicode);

    // Send the email message
    using (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "password"))
    {
        client.SecurityOptions = SecurityOptions.SSLExplicit;
        client.Send(message);
    }
}
```
