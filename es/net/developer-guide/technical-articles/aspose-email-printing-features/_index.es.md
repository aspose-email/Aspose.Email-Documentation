---
title: "Funciones de Impresión de Aspose.Email"
url: /es/net/aspose-email-printing-features/
weight: 150
type: docs
---

## **Funciones de Impresión**
El espacio de nombres [Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) proporciona un conjunto rico de funciones para imprimir mensajes de correo en diferentes formatos (XPS o TIFF) y configurar diseños de página. Este artículo las describe. Hay varias opciones sobre cómo se puede imprimir un mensaje de correo desde Aspose.Email:

1. Imprimir solo el cuerpo del mensaje.
1. Imprimir el cuerpo del mensaje y los encabezados.
1. Imprimir un cuerpo HTML.
1. Configurar el diseño de la página.
1. Ajustar automáticamente un TIFF a la impresora.
1. Ajustar el DPI objetivo para el TIFF de salida.
### **Imprimir el Cuerpo del Mensaje**
El siguiente fragmento de código muestra cómo crear un mensaje e imprimirlo sin encabezados primero en un archivo XPS y luego en un archivo TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Imprimir Encabezados y Cuerpo del Mensaje**
El siguiente fragmento de código muestra cómo mostrar los encabezados e imprimirlos así como el cuerpo del mensaje, cambiando los [FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) a [MailInfo](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Imprimir Mensaje con Cuerpo HTML**
Los mensajes con un cuerpo HTML también se pueden imprimir. El siguiente fragmento de código muestra cómo imprimir un mensaje con cuerpo HTML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Configurar el Diseño de Página para Imprimir**
[Aspose.Email.Printing.MailPrinter](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter) proporciona controles para establecer las siguientes propiedades del diseño de la página:

|**Propiedad**|**Descripción**|**Valor por Defecto**|
| :- | :- | :- |
|[FormattingFlags](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Mostrar u ocultar detalles del mensaje.|Ninguno [1]|
|[MarginTop](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Obtener o establecer el margen superior.|0.5|
|[MarginLeft](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Obtener o establecer el margen izquierdo.|0.5|
|[MarginBottom](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Obtener o establecer el margen inferior.|0.5|
|[MarginRight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Obtener o establecer el margen derecho.|0.5|
|[PageUnit](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Obtener o establecer unidades de medida.|Pulgada [2]|
|[PageHeight](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Obtener o establecer la altura de la página.|11.69|
|[PageWidth](https://apireference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Obtener o establecer el ancho de la página.|8.27|
- Hay dos banderas: MailInfo y Ninguna
- Las unidades de página pueden ser una de Pulgada, Píxel, Punto, Cm o Milímetros.

El siguiente fragmento de código utiliza configuraciones arbitrarias para ilustrar cómo se utilizan estas propiedades. Configura una página de 20 cm de alto y 8 cm de ancho, con márgenes de 2 cm.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Ajustar Automáticamente un TIFF**
[Aspose.Email.Printing](https://apireference.aspose.com/net/email/aspose.email.printing/) proporciona la propiedad [MessageFormattingFlags.AutoFitWidth](https://apireference.aspose.com/net/email/aspose.email.printing/messageformattingflags) que permite ajustar automáticamente el TIFF a la impresora. El siguiente fragmento de código muestra cómo usar Ajustar automáticamente.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Ajustar DPI Objetivo para TIFF de Salida**
El siguiente fragmento de código muestra cómo utilizar DPI para TIFF de salida.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}