---
title: "Использование документа Microsoft Word в качестве тела сообщения и отправка электронной почты"
url: /ru/net/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---

Эта статья показывает, как использовать документ Microsoft Word в качестве тела электронной почты и отправить его получателям. Пример документа представляет собой счет-фактуру из базы данных Northwind, экспортированную в формат Microsoft Word. Aspose.Email для .NET обрабатывает сетевые протоколы и функции Microsoft Outlook, но не может работать с документами Microsoft Word. Чтобы обойти это, в примерах этой статьи используется [Aspose.Words для .NET](https://products.aspose.com/words/net/) для загрузки документа Word и конвертации его в формат MHTML. Aspose.Email для .NET использует документ MHTML в теле электронной почты.
## **Использование документов Microsoft Word в качестве тела электронной почты**
Программные примеры ниже иллюстрируют, как отправить документ Word в качестве тела электронной почты, используя Aspose.Words для .NET и Aspose.Email для .NET:

1. Загрузите документ Microsoft Word с использованием класса [Document](https://apireference.aspose.com/words/net/aspose.words/document) из Aspose.Words для .NET.
1. Сохраните его в формате MHTML.
1. Загрузите документ MHTML с использованием класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) из Aspose.Email для .NET, чтобы установить тело электронной почты.
1. Установите другие свойства сообщения, используя различные свойства и методы класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Отправьте электронное письмо, используя класс [SMTPClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) из Aspose.Email для .NET.

Исходный документ, счет-фактура, экспортированный в Microsoft Word из примера Microsoft Northwind, представлен ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Когда сообщение было отправлено и получено в Microsoft Outlook, оно выглядит как сообщение ниже.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

HTML-форматирование и изображения сохраняются, как в оригинальном исходном документе, при просмотре в Outlook или в веб-клиенте электронной почты, таком как Gmail или Hotmail. Ниже представлено скриншот сообщения при открытии с помощью Gmail в браузере Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

Следующий фрагмент кода показывает, как использовать документ Microsoft Word в качестве тела сообщения и отправить электронное письмо, используя экземпляр класса [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

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
    message.Subject = "Отправка счета по электронной почте";
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