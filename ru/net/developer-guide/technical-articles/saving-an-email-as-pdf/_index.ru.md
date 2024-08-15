---
title: "Сохранение электронного письма в формате PDF"
url: /ru/net/saving-an-email-as-pdf/
weight: 230
type: docs
---


В этой статье показано, как преобразовать сообщение электронной почты в PDF с помощью Aspose.Email. Aspose.Email для .NET занимается сетевыми протоколами и функциями Microsoft Outlook и не может обрабатывать прямое преобразование в PDF. Чтобы решить эту проблему, в примерах этой статьи используется Aspose.Email для преобразования сообщения электронной почты в поток MHTML, а затем с помощью Aspose.Words для.NET загрузить поток MHTML и затем сохранить его в формате PDF. Сообщение электронной почты также может содержать вложения. Поскольку каждое вложение может иметь разные типы медиафайлов, Aspose.Email игнорирует эти вложения при преобразовании в MHTML, то есть только встроенные изображения в сообщении будут частью MHTML, а любые обычные вложения будут игнорироваться.
## **Преобразование сообщения электронной почты в PDF**
Следующий код показывает преобразование сообщений электронной почты в PDF с помощью Aspose.Email в сочетании с Aspose.Words для .NET. Это включает в себя следующие шаги:

1. Загрузите сообщение электронной почты, используя [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage)
1. Сохраните сообщение электронной почты в MemoryStream в формате MHTML
1. Загрузите трансляцию с помощью Aspose.Words
1. Сохранить сообщение в формате PDF

Исходное сообщение электронной почты можно увидеть следующим образом:

![todo:image_alt_text](saving-an-email-as-pdf_1.png)

Конвертированный PDF-файл показан на следующем рисунке:

![todo:image_alt_text](saving-an-email-as-pdf_2.png)

В следующем фрагменте кода показано, как конвертировать сообщения электронной почты в PDF.

```csharp
string dataDir = RunExamples.GetDataDir_KnowledgeBase();
MailMessage mailMsg = MailMessage.Load(dataDir + "message3.msg");
MemoryStream ms = new MemoryStream();
mailMsg.Save(ms, Aspose.Email.SaveOptions.DefaultMhtml);

// create an instance of LoadOptions and set the LoadFormat to Mhtml
var loadOptions = new Aspose.Words.Loading.LoadOptions();
loadOptions.LoadFormat = LoadFormat.Mhtml;

// create an instance of Document and load the MTHML from MemoryStream
var document = new Aspose.Words.Document(ms, loadOptions);

// create an instance of HtmlSaveOptions and set the SaveFormat to Html
var saveOptions = new Aspose.Words.Saving.PdfSaveOptions();
document.Save(dataDir + "SaveEmailAsPDF_out.pdf", saveOptions);
```
