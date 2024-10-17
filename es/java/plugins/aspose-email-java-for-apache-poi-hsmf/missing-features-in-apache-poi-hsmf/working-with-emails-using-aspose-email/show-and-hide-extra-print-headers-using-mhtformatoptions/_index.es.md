---
title: "Mostrar y Ocultar Encabezados de Impresión Extra usando MHTFormatOptions"
url: /es/java/show-and-hide-extra-print-headers-using-mhtformatoptions/
weight: 40
type: docs
---

## **Aspose.Email - Mostrar y Ocultar Encabezados de Impresión Extra usando MHTFormatOptions**
Los encabezados de impresión extra se pueden mostrar u ocultar con MhtFormatOptions y MailMessageSaveOptions. MhtFormatOptions es un enumerador que contiene dos miembros: WriteCompleteEmailAddressToMht y HideExtraPrintHeader. MhtFormatOptions se utiliza con MhtMessageFormatter ya que el método público MhtMessageFormatter.Format con el argumento writeCompleteEmailAddress está obsoleto ahora.

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
## **Descargar Código en Ejecución**
Descarga **Mostrar y Ocultar Encabezados de Impresión Extra usando MHTFormatOptions** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)