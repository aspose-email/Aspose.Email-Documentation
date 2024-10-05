---
title: "Конвертация файла сообщения Outlook (MSG) в изображение TIFF"
url: /ru/net/converting-outlook-message-file-msg-to-tiff-image/
weight: 130
type: docs
---


В этой статье мы покажем вам, как конвертировать файл MSG Outlook в изображение TIFF.

1. Сначала прочитайте файл MSG и конвертируйте его в формат MHTML с помощью Aspose.Email для .NET. Используйте класс [Aspose.Email.MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) для загрузки файла сообщения.
1. После загрузки файла вызовите метод [MailMessage.Save()](https://apireference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) и сохраните его в поток в формате MHTML.
1. Используйте Aspose.Words для .NET для конвертации потока MHTML в TIFF. Используйте класс [Aspose.Words.Document](https://apireference.aspose.com/net/words/aspose.words/document) для загрузки потока MHTML.
1. Наконец, вызовите метод [Document.Save()](https://apireference.aspose.com/net/words/aspose.words/document/methods/save/index) для сохранения документа MHTML в TIFF.

Если документ содержит несколько страниц, будет создан файл TIFF с несколькими страницами. Приведенные ниже фрагменты кода показывают, как конвертировать файл сообщения Outlook (MSG) в изображение TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}