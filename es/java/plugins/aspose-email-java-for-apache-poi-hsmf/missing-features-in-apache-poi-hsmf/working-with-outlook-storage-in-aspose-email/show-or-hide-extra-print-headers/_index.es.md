---
title: "Mostrar u Ocultar Encabezados de Impresión Adicionales"
url: /es/java/show-or-hide-extra-print-headers/
weight: 50
type: docs
---

## **Aspose.Email - Mostrar u Ocultar Encabezados de Impresión Adicionales**
Los encabezados de impresión adicionales se pueden mostrar u ocultar con MhtFormatOptions y MailMessageSaveOptions. MhtFormatOptions es un enumerador que contiene dos miembros - WriteCompleteEmailAddressToMht y HideExtraPrintHeader. MhtFormatOptions se utiliza con MhtMessageFormatter como el método público MhtMessageFormatter.Format con el argumento writeCompleteEmailAddress que ahora está obsoleto.

**Java**

``` java

 MailMessage message = MailMessage.load(dataDir + "message.eml");

String encodedPageHeader = "<div><div class=3D'page=Header'>&quot;Panditharatne, Mithra&quot; &lt;mithra=2Epanditharatne@cibc==2Ecom&gt;<hr/></div>";

int saveOptions =  MailMessageSaveOptions.HideExtraPrintHeader;

message.save(dataDir + "AsposeHideExtraHeaders.mhtml", MailMessageSaveType.getMHtmlFormat(), saveOptions);

```
## **Descargar Código Ejecutable**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/printheaders/AsposeShowHidePrintHeaders.java)