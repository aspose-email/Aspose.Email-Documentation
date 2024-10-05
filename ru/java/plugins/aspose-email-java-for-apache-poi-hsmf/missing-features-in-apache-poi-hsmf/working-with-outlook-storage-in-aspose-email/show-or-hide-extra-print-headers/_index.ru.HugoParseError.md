---
title: Показать или Скрыть Дополнительные Заголовки Печати
type: docs
weight: 50
url: /java/show-or-hide-extra-print-headers/
---

## **Aspose.Email - Показать или Скрыть Дополнительные Заголовки Печати**
Дополнительные заголовки печати могут быть показаны или скрыты с помощью MhtFormatOptions и MailMessageSaveOptions. MhtFormatOptions является перечислением, которое содержит два члена - WriteCompleteEmailAddressToMht и HideExtraPrintHeader. MhtFormatOptions используется с MhtMessageFormatter как публичный метод MhtMessageFormatter.Format, в котором аргумент writeCompleteEmailAddress в настоящее время устарел.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Скачать Исполняемый Код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать Пример Кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)