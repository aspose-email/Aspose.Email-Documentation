---
title: "Usar una hoja de cálculo de Microsoft Excel como el cuerpo del mensaje y enviar correo electrónico"
url: /es/net/using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email/
weight: 160
type: docs
---


Este artículo utiliza un libro de trabajo de Microsoft Excel como el cuerpo del correo electrónico y lo envía a los destinatarios. Aspose.Email para .NET se ocupa de los protocolos de red y las características de Microsoft Outlook y no puede manejar libros de trabajo de Microsoft Excel. Para superarlo, los ejemplos en este artículo utilizan Aspose.Cells para .NET para cargar el libro de trabajo de Excel y convertirlo en un flujo HTML. Luego, Aspose.Email para .NET utiliza el flujo HTML en el cuerpo del correo electrónico. El ejemplo de programación muestra cómo enviar una hoja de cálculo de Excel como cuerpo del correo electrónico utilizando Aspose.Cells para .NET y Aspose.Email para .NET.

1. Cargando un libro de trabajo de Microsoft Excel utilizando la clase Workbook de Aspose.Cells
1. Guardar el libro de trabajo cargado en MemoryStream en formato HTML
1. Obtener el HTML del flujo como String
1. Definir un nuevo objeto MailMessage y establecer su HtmlBody en el contenido HTML del paso 3
1. Enviar el correo electrónico utilizando la clase SmtpClient de Aspose.Email para .NET

El libro de trabajo de Excel fuente se puede ver de la siguiente manera:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_1.png)



Cuando el mensaje ha sido enviado y recibido en Microsoft Outlook, se ve como el mensaje a continuación:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_2.png)



El siguiente fragmento de código muestra cómo enviar una hoja de cálculo de MS Excel como el cuerpo del mensaje y enviar correo electrónico.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendExcelWorksheetAsMessageBody-SendExcelWorksheetAsMessageBody.cs" >}}