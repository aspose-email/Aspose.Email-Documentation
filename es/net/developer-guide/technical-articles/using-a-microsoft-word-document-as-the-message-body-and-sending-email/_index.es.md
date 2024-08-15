---
title: "Uso de un documento de Microsoft Word como cuerpo del mensaje y envío de correo electrónico"
url: /es/net/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---


En este artículo se muestra cómo usar un documento de Microsoft Word como cuerpo del correo electrónico y enviarlo a los destinatarios. El documento de muestra es una factura de venta de la muestra de la base de datos Northwind, exportada al formato Microsoft Word. Aspose.Email para.NET utiliza los protocolos de red y las funciones de Microsoft Outlook y no puede gestionar documentos de Microsoft Word. Para superar esto, los ejemplos de este artículo utilizan [Aspose.Words para.NET](https://products.aspose.com/words/net/) para cargar el documento de Word y convertirlo a formato MHTML. Aspose.Email para .NET usa el documento MHTML en el cuerpo del correo electrónico.
## **Uso de documentos de Microsoft Word como cuerpo de correo electrónico**
Los siguientes ejemplos de programación muestran cómo enviar un documento de Word como cuerpo de correo electrónico mediante Aspose.Words para .NET y Aspose.Email para .NET:

1. Cargue un documento de Microsoft Word con Aspose.Word para.NET [Document](https://apireference.aspose.com/words/net/aspose.words/document) class.
1. Guárdalo en formato MHTML.
1. Cargue el documento MHTML usando Aspose.Email para.NET [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) clase para configurar el cuerpo del correo electrónico.
1. Establezca otras propiedades del mensaje utilizando diferentes [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) propiedades y métodos de clase.
1. Envía el correo electrónico usando Aspose.Email para .NET [SMTPClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) class.

El documento fuente, una factura de venta exportada a Microsoft Word desde la muestra de Microsoft Northwind, se puede ver a continuación.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Cuando el mensaje se haya enviado y recibido en Microsoft Outlook, tendrá el mismo aspecto que el siguiente mensaje.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

El formato HTML y las imágenes se conservan como en el documento original cuando se ven en Outlook o en un cliente de correo electrónico web como Gmail o Hotmail. A continuación se muestra una captura de pantalla del mensaje cuando se abre con Gmail en un navegador Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

El siguiente fragmento de código muestra cómo usar un documento de Microsoft Word como cuerpo del mensaje y enviar un correo electrónico mediante [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) instancia de clase.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Load a Word document from disk and save it to stream as MHTML
Document wordDocument = new Document(folderPath + "invoice.docx");
MemoryStream mhtmlStream = new MemoryStream();
wordDocument.Save(mhtmlStream, SaveFormat.Mhtml);

// Load the MHTML in a MailMessage object
mhtmlStream.Position = 0;
using (MailMessage message = MailMessage.Load(mhtmlStream, new MhtmlLoadOptions()))
{
    message.Subject = "Sending Invoice by Email";
    message.From = "sender@gmail.com";
    message.To = "recipient@gmail.com";

    // Save the message in MSG format to disk
    message.Save(folderPath + "WordDocAsEmailBody_out.msg", SaveOptions.DefaultMsgUnicode);

    // Send the email message
    using (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "password"))
    {
        client.SecurityOptions = SecurityOptions.SSLExplicit;
        client.Send(message);
    }
}
```
