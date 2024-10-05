---
title: "Сохранение MSG в PDF"
url: /ru/java/saving-a-msg-as-pdf/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

В этой статье показано, как преобразовать электронное сообщение в PDF с помощью Aspose.Email. Aspose.Email для Java обрабатывает функции Microsoft Outlook и не может выполнять прямое преобразование в PDF. Чтобы обойти это, в примерах в этой статье используется Aspose.Email для преобразования электронного сообщения в поток MHTML, а затем используется Aspose.Words для Java для загрузки потока MHTML и последующего сохранения его в PDF.

{{% /alert %}} {{% alert color="primary" %}} 

Электронное сообщение также может содержать вложения. Поскольку каждое вложение может быть разных типов медиа, Aspose.Email игнорирует эти вложения при преобразовании в MHTML, т.е. только встроенные изображения в сообщении будут частью MHTML, а любые обычные вложения будут проигнорированы.

{{% /alert %}} 
## **Преобразование электронного сообщения в PDF**
Следующий код показывает, как преобразовать электронное сообщение в PDF с помощью Aspose.Email в сочетании с Aspose.Words для Java. Это включает в себя следующие шаги:

1. Загрузите электронное сообщение с помощью MailMessage
2. Сохраните электронное сообщение в MemoryStream в формате MHTML
3. Загрузите поток с помощью Aspose.Words
4. Сохраните сообщение в PDF

Исходное электронное сообщение можно увидеть следующим образом:

|![todo:image_alt_text](saving-a-msg-as-pdf_1.png)|
| :- |
|**Рисунок: Исходный файл MSG** |


|![todo:image_alt_text](saving-a-msg-as-pdf_2.png)|
| :- |
|**Рисунок: Преобразованный файл PDF** |
**Java**

``` java

 static void EmailToPdf(String emailPath) throws Exception

{

       FileInputStream fstream=new FileInputStream(emailPath);

       MailMessage eml = MailMessage.load(fstream);

       //Сохраните сообщение в выходной поток в формате MHTML

       ByteArrayOutputStream emlStream = new ByteArrayOutputStream();

       eml.save(emlStream, SaveOptions.getDefaultMhtml());

       //Загрузите поток в документ Word

       LoadOptions lo = new LoadOptions();

       lo.setLoadFormat(LoadFormat.MHTML);

       Document doc = new Document(new ByteArrayInputStream(emlStream.toByteArray()), lo);

       //Сохраните на диск

       doc.save("About Aspose.Pdf", SaveFormat.PDF);

       //или Сохраните в поток

       ByteArrayOutputStream foStream = new ByteArrayOutputStream();

       doc.save(foStream, SaveFormat.PDF);

}

```