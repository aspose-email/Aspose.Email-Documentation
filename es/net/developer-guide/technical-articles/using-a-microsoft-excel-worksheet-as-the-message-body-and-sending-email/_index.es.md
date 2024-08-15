---
title: "Uso de una hoja de cálculo de Microsoft Excel como cuerpo del mensaje y envío de correo electrónico"
url: /es/net/using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email/
weight: 160
type: docs
---


Este artículo usa un libro de Microsoft Excel como cuerpo del correo electrónico y lo envía a los destinatarios. Aspose.Email para .NET se ocupa de los protocolos de red y las funciones de Microsoft Outlook y no puede gestionar libros de Microsoft Excel. Para solucionar este problema, en los ejemplos de este artículo se utiliza Aspose.Cells para.NET para cargar el libro de Excel y convertirlo en una secuencia HTML. Aspose.Email para .NET, entonces, usa la secuencia HTML en el cuerpo del correo electrónico. En el ejemplo de programación se muestra cómo enviar una hoja de cálculo de Excel como cuerpo de correo electrónico mediante Aspose.Cells para.NET y Aspose.Email para.NET

1. Carga de un libro de trabajo de Microsoft Excel con la clase Workbook de Aspose.Cells
1. Guarde el libro de trabajo cargado en MemoryStream en formato HTML
1. Obtenga el HTML de la transmisión como cadena
1. Defina un nuevo objeto MailMessage y establezca su HTMLBody en el contenido HTML del paso 3
1. Envíe el correo electrónico mediante Aspose.Email para la clase SmtpClient de.NET

El libro de Excel de origen se puede ver de la siguiente manera:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_1.png)



Cuando el mensaje se haya enviado y recibido en Microsoft Outlook, tendrá el siguiente aspecto:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_2.png)



El siguiente fragmento de código muestra cómo enviar una hoja de cálculo de MS Excel como cuerpo del mensaje y cómo enviar un correo electrónico.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendExcelWorksheetAsMessageBody-SendExcelWorksheetAsMessageBody.cs" >}}
