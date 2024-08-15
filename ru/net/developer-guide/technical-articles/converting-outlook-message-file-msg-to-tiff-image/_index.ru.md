---
title: "Преобразование файла сообщений Outlook (MSG) в изображение TIFF"
url: /ru/net/converting-outlook-message-file-msg-to-tiff-image/
weight: 130
type: docs
---


В этой статье мы покажем вам, как преобразовать файл Outlook MSG в изображение TIFF.

1. Сначала прочтите файл MSG и преобразуйте его в формат MHTML с помощью Aspose.Email для .NET. Используйте [Aspose.Email.MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) класс для загрузки файла сообщения.
1. После загрузки файла вызовите [MailMessage.Save()](https://apireference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) метод и сохраните его в потоковом режиме в формате MHTML.
1. Используйте Aspose.Words для.NET для преобразования потока MHTML в формат TIFF. Используйте [Aspose.Words.Document](https://apireference.aspose.com/net/words/aspose.words/document) класс для загрузки потока MHTML.
1. Наконец, позвоните [Document.Save()](https://apireference.aspose.com/net/words/aspose.words/document/methods/save/index) метод сохранения документа MHTML в формате TIFF.

Если документ содержит несколько страниц, создается многостраничный файл TIFF. В приведенных ниже фрагментах кода показано, как преобразовать файл сообщений Outlook (MSG) в изображение TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}
