---
title: "Сохранение Email в PDF"
url: /ru/net/saving-an-email-as-pdf/
weight: 230
type: docs
---

В этой статье показано, как конвертировать сообщение электронной почты в PDF с помощью Aspose.Email. Aspose.Email для .NET работает с сетевыми протоколами и функциями Microsoft Outlook и не может выполнять прямую конвертацию в PDF. Чтобы обойти это ограничение, в примерах этой статьи используется Aspose.Email для преобразования сообщения электронной почты в поток MHTML, а затем используется Aspose.Words для .NET для загрузки потока MHTML и сохранения его в формате PDF. Сообщение электронной почты также может содержать вложения. Поскольку каждое вложение может иметь разные типы медиа, Aspose.Email игнорирует эти вложения при конвертации в MHTML, т.е. только встроенные изображения в сообщении будут частью MHTML, а все обычные вложения будут проигнорированы.
## **Конвертация сообщения электронной почты в PDF**
Следующий код показывает, как конвертировать сообщения электронной почты в PDF, используя Aspose.Email в сочетании с Aspose.Words для .NET. Это включает в себя следующие шаги:

1. Загрузите сообщение электронной почты, используя [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage)
1. Сохраните сообщение электронной почты в MemoryStream как MHTML
1. Загрузите поток с помощью Aspose.Words
1. Сохраните сообщение как PDF

Исходное сообщение электронной почты можно увидеть следующим образом:

![todo:image_alt_text](saving-an-email-as-pdf_1.png)

Преобразованный PDF представлен на следующем изображении:

![todo:image_alt_text](saving-an-email-as-pdf_2.png)

Следующий фрагмент кода показывает, как конвертировать сообщения электронной почты в PDF.

```csharp
string dataDir = RunExamples.GetDataDir_KnowledgeBase();
MailMessage mailMsg = MailMessage.Load(dataDir + "message3.msg");
MemoryStream ms = new MemoryStream();
mailMsg.Save(ms, Aspose.Email.SaveOptions.DefaultMhtml);

// создайте экземпляр LoadOptions и установите LoadFormat в Mhtml
var loadOptions = new Aspose.Words.Loading.LoadOptions();
loadOptions.LoadFormat = LoadFormat.Mhtml;

// создайте экземпляр Document и загрузите MTHML из MemoryStream
var document = new Aspose.Words.Document(ms, loadOptions);

// создайте экземпляр HtmlSaveOptions и установите SaveFormat в Html
var saveOptions = new Aspose.Words.Saving.PdfSaveOptions();
document.Save(dataDir + "SaveEmailAsPDF_out.pdf", saveOptions);
```