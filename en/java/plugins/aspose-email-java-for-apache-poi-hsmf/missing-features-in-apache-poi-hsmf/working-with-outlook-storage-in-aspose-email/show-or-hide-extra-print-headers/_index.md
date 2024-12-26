---
title: Show or Hide Extra Print Headers
ArticleTitle: Show or Hide Extra Print Headers
type: docs
weight: 50
url: /java/show-or-hide-extra-print-headers/
---

## **Aspose.Email - Show or Hide Extra Print Headers**
Extra print headers can be shown or hidden with MhtFormatOptions and MailMessageSaveOptions. MhtFormatOptions is an enumerator which contains two members - WriteCompleteEmailAddressToMht and HideExtraPrintHeader. MhtFormatOptions is used withMhtMessageFormatter as the public method MhtMessageFormatter.Format with argument writeCompleteEmailAddress is obsolete now.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
