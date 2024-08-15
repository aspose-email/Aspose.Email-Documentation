---
title: "Показать или скрыть дополнительные заголовки для печати"
url: /ru/java/show-or-hide-extra-print-headers/
weight: 50
type: docs
---

## **Aspose.Email - Показать или скрыть дополнительные заголовки для печати**
Дополнительные заголовки для печати можно показать или скрыть с помощью MhtFormatOptions и MailMessageSaveOptions. MHTFormatOptions — это перечислитель, состоящий из двух элементов: «Записать полный адрес электронной почты в HT» и «HideExtraPrintHeader». MHTFormatOptions используется вместе с MHTMessageFormatter в качестве публичного метода MHTMessageFormatter.Формат с аргументом WriteCompleteEmailAddress теперь устарел.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
