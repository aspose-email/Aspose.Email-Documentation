---
title: "Mostrar u ocultar encabezados de impresión adicionales"
url: /es/java/show-or-hide-extra-print-headers/
weight: 50
type: docs
---

## **Aspose.Email - Mostrar u ocultar encabezados de impresión adicionales**
Los encabezados de impresión adicionales se pueden mostrar u ocultar con mhtFormatOptions y MailMessageSaveOptions. MhtFormatOptions es un enumerador que contiene dos miembros: WriteCompleteEmailAddressToMht y HideExtraPrintHeader. MhtFormatOptions se usa con MhtMessageFormatter como método público. MhtMessageFormatter.format con el argumento writeCompleteEmailAddress ya está obsoleto.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
