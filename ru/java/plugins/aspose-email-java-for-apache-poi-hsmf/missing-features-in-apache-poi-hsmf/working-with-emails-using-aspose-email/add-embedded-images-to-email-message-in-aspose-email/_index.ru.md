---
title: "Добавить встроенные изображения в электронное сообщение в Aspose.Email"
url: /ru/java/add-embedded-images-to-email-message-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Добавить встроенные изображения в электронное сообщение**
С Aspose.Email разработчики на Java могут легко встроить любое изображение в электронное сообщение, а также приложить его, как обсуждается в [Управление вложениями в электронном сообщении](/email/java/working-with-message-attachments). Для встраивания изображения Aspose.Email использует специализированный класс, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Установить HTML тело. Оно также содержит тег <img> с cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>Эта строка жирным шрифтом.</b> <br/> <br/>"

        + "<font color=blue>Эта строка синего цвета</font><br><br>" +

        "Вот встроенное изображение.<img src=cid:companylogo>");

// Добавить связанный ресурс

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Добавить связанный ресурс в коллекцию связанных ресурсов сообщения

message.getLinkedResources().addItem(res);

```
## **Скачать рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}} 

Для получения дополнительных деталей посетите [Добавить встроенные изображения в электронное сообщение](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}