---
title: "Funciones de impresión de Aspose.Email."
url: /es/net/aspose-email-printing-features/
weight: 150
type: docs
---

## **Funciones de impresión**
The [Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) El espacio de nombres proporciona un amplio conjunto de funciones para imprimir mensajes de correo en diferentes formatos (XPS o TIFF) y configurar diseños de página. En este artículo se describen. Hay varias opciones para imprimir un mensaje de correo electrónico desde Aspose.Email:

1. Imprimir únicamente el cuerpo del mensaje.
1. Imprimir el cuerpo y los encabezados del mensaje.
1. Impresión de un cuerpo HTML.
1. Configuración del diseño de la página.
1. Ajuste automáticamente un TIFF a la impresora.
1. Ajuste el DPI objetivo para el TIFF de salida.
### **Impresión del cuerpo del mensaje**
El siguiente fragmento de código muestra cómo crear un mensaje e imprimirlo sin encabezados primero en un archivo XPS y, a continuación, en un archivo TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Impresión de los encabezados y el cuerpo de los mensajes**
El siguiente fragmento de código muestra cómo mostrar los encabezados e imprimirlos, así como el cuerpo del mensaje, cambiar el [FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) to [MailInfo](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Impresión de mensajes con cuerpo HTML**
Los mensajes con un cuerpo HTML también se pueden imprimir. El siguiente fragmento de código muestra cómo imprimir un mensaje con un cuerpo HTML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Configuración del diseño de página para la impresión**
[Aspose.Email.Printing.MailPrinter](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter) proporciona controles para establecer las siguientes propiedades del diseño de página:

|**Property**|**Description**|**Valor predeterminado**|
|: - |: - |: - |
|[FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Mostrar u ocultar los detalles del mensaje. |Ninguno [1] |
|[MarginTop](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Obtener o establecer el margen superior.|0.5|
|[MarginLeft](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Obtener o establecer el margen izquierdo.|0.5|
|[MarginBottom](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Obtener o establecer el margen inferior.|0.5|
|[MarginRight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Obtenga o establezca el margen derecho.|0.5|
|[PageUnit](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Obtenga o defina las unidades de medida. |Pulgadas [2] |
|[PageHeight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Obtenga o establezca la altura de la página.|11.69|
|[PageWidth](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Obtiene o establece el ancho de la página.|8.27|
- Hay dos banderas: MailInfo y None
- Las unidades de página pueden ser pulgadas, píxeles, puntos, centímetros o milímetros.

El fragmento de código que sigue usa configuraciones arbitrarias para ilustrar cómo se usan estas propiedades. Crea una página de 20 cm de alto y 8 cm de ancho, con márgenes de 2 cm.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Ajustar automáticamente un TIFF**
[Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) proporciona la [MessageFormattingFlags.AutoFitWidth](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags) propiedad que le permite ajustar automáticamente el TIFF a la impresora. El siguiente fragmento de código muestra cómo utilizar el ajuste automático.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Ajustar el DPI de destino para el TIFF de salida**
El siguiente fragmento de código muestra cómo usar DPI para el TIFF de salida.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}
