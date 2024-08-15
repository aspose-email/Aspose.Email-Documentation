---
title: "Добавьте встроенные изображения в сообщение электронной почты в Aspose.Email"
url: /ru/java/add-embedded-images-to-email-message-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - добавление встроенных изображений в сообщение электронной почты**
С помощью Aspose.Email разработчики Java могут легко вставить любое изображение в сообщение электронной почты, а также прикрепить его, как описано в [Управление вложениями в сообщении электронной почты](/email/java/working-with-message-attachments). Для встраивания изображения Aspose.Email использует специализированный класс, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Set Html body. It also contains <img> tag with cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>"

        + "<font color=blue>This line is in blue color</font><br><br>" +

        "Here is an embedded image.<img src=cid:companylogo>");

// Add linked resource

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Add Linked resource to the message's Linked resource collection

message.getLinkedResources().addItem(res);

```
## **Загрузить рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Добавить встроенные изображения в сообщение электронной почты](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}
