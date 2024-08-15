---
title: "Mostrar y ocultar encabezados de impresión adicionales mediante MhtFormatOptions"
url: /es/java/show-and-hide-extra-print-headers-using-mhtformatoptions/
weight: 40
type: docs
---

## **Aspose.Email: muestra y oculta los encabezados de impresión adicionales usando MhtFormatOptions**
Los encabezados de impresión adicionales se pueden mostrar u ocultar con mhtFormatOptions y MailMessageSaveOptions. MhtFormatOptions es un enumerador que contiene dos miembros: WriteCompleteEmailAddressToMht y HideExtraPrintHeader. MhtFormatOptions se usa con MhtMessageFormatter como método público. MhtMessageFormatter.format con el argumento writeCompleteEmailAddress ya está obsoleto.

**Java**

```java

 String dataPath = "src/asposefeatures/programmingemail/showhideextraprintheaders/data/";

String pageHeader = "<div><div class='pageHeader'>&quot;Panditharatne, Mithra&quot; &lt;mithra.panditharatne@cibc.com&gt;<hr/></div>";

MailMessage message = MailMessage.load(dataPath + "message.eml");

MhtMessageFormatter mailFormatter = new MhtMessageFormatter();

int options =  MhtFormatOptions.HideExtraPrintHeader | MhtFormatOptions.WriteCompleteEmailAddressToMht;

mailFormatter.format(message, options);

if(!message.getHtmlBody().contains(pageHeader))

	System.out.println("True");

else

	System.out.println("False");

```
## **Descargar Running Code**
Download **Mostrar y ocultar encabezados de impresión adicionales mediante MhtFormatOptions** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
