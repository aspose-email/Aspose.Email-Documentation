---
title: "Сохранение файла MSG в формате PDF"
url: /ru/java/saving-a-msg-as-pdf/
weight: 30
type: docs
---

{{% alert color="primary" %}}

В этой статье показано, как преобразовать сообщение электронной почты в PDF с помощью Aspose.Email.
Aspose.Email для Java предоставляет функции Microsoft Outlook и не поддерживает прямое преобразование в PDF. Чтобы решить эту проблему, в примерах, приведенных в этой статье, используйте Aspose.Email для преобразования сообщения электронной почты в поток MHTML, а затем используйте Aspose.Words для Java для загрузки потока MHTML и последующего сохранения его в формате PDF.

{{% /alert %}} {{% alert color="primary" %}}

Сообщение электронной почты также может содержать вложения. Поскольку каждое вложение может иметь различный тип носителя, Aspose.Email игнорирует эти вложения при преобразовании в MHTML, то есть только встроенные изображения в сообщении будут частью MHTML, а любые обычные вложения будут игнорироваться.

{{% /alert %}}
## **Конвертировать сообщение электронной почты в PDF**
Следующий код показывает преобразование сообщения электронной почты в PDF с помощью Aspose.Email в сочетании с Aspose.Words для Java. Это включает в себя следующие шаги:

1. Загрузите сообщение электронной почты с помощью MailMessage
1. Сохраните сообщение электронной почты в MemoryStream в формате MHTML
1. Загрузите трансляцию с помощью Aspose.Words
1. Сохранить сообщение в формате PDF

Исходное сообщение электронной почты можно увидеть следующим образом:

|![todo:image_alt_text](saving-a-msg-as-pdf_1.png)|
|: - |
|**Рис.: Исходный MSG-файл** |


|![todo:image_alt_text](saving-a-msg-as-pdf_2.png)|
|: - |
|**Рис.: Конвертированный PDF-файл** |
**Java**

``` java

 static void EmailToPdf(String emailPath) throws Exception

{

       FileInputStream fstream=new FileInputStream(emailPath);

       MailMessage eml = MailMessage.load(fstream);

       //Save the Message to output stream in MHTML format

       ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

       eml.save(emlStream, SaveOptions.getDefaultMhtml());

       //Load the stream in Word document

       LoadOptions lo = new LoadOptions();

       lo.setLoadFormat(LoadFormat.MHTML);

       Document doc = new Document(new ByteArrayInputStream(emlStream.toByteArray()), lo);

       //Save to disc

       doc.save("About Aspose.Pdf", SaveFormat.PDF);

       //or Save to stream

       ByteArrayOutputStream foStream = new ByteArrayOutputStream();

       doc.save(foStream, SaveFormat.PDF);

}

```
