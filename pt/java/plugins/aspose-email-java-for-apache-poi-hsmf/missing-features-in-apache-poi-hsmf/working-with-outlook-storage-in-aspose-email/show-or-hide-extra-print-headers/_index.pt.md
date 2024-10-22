---
title: "Mostrar ou Ocultar Cabeçalhos de Impressão Extras"
url: /pt/java/show-or-hide-extra-print-headers/
weight: 50
type: docs
---

## **Aspose.Email - Mostrar ou Ocultar Cabeçalhos de Impressão Extras**
Os cabeçalhos de impressão extras podem ser mostrados ou ocultados com MhtFormatOptions e MailMessageSaveOptions. MhtFormatOptions é um enumerador que contém dois membros - WriteCompleteEmailAddressToMht e HideExtraPrintHeader. MhtFormatOptions é utilizado comMhtMessageFormatter como o método público MhtMessageFormatter.Format com o argumento writeCompleteEmailAddress está obsoleto agora.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Código de Download em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Código de Exemplo para Download**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)