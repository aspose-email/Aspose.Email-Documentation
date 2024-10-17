---
title: "Usando un Documento de Microsoft Word como Cuerpo del Mensaje y Enviando Correo Electrónico"
url: /es/net/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---

Este artículo te muestra cómo utilizar un documento de Microsoft Word como el cuerpo del correo electrónico y enviarlo a los destinatarios. El documento de muestra es una factura de ventas de la base de datos de Northwind, exportada al formato de Microsoft Word. Aspose.Email para .NET se encarga de los protocolos de red y las funciones de Microsoft Outlook y no puede manejar documentos de Microsoft Word. Para superar esto, las muestras en este artículo utilizan [Aspose.Words para .NET](https://products.aspose.com/words/net/) para cargar el documento de Word y convertirlo al formato MHTML. Aspose.Email para .NET utiliza el documento MHTML en el cuerpo del correo electrónico.

## **Usando Documentos de Microsoft Word como Cuerpo del Correo Electrónico**
Las muestras de programación a continuación ilustran cómo enviar un documento de Word como un cuerpo de correo electrónico utilizando Aspose.Words para .NET y Aspose.Email para .NET:

1. Carga un documento de Microsoft Word utilizando la clase [Document](https://apireference.aspose.com/words/net/aspose.words/document) de Aspose.Word para .NET.
1. Guárdalo en formato MHTML.
1. Carga el documento MHTML utilizando la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) de Aspose.Email para .NET para establecer el cuerpo del correo electrónico.
1. Establece otras propiedades del mensaje utilizando diferentes propiedades y métodos de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Envía el correo electrónico utilizando la clase [SMTPClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) de Aspose.Email para .NET.

El documento fuente, una factura de ventas exportada a Microsoft Word desde la muestra de Microsoft Northwind, se puede ver a continuación.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Cuando se ha enviado y recibido el mensaje en Microsoft Outlook, se ve como el mensaje a continuación.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

El formato HTML y las imágenes se conservan como en el documento fuente original cuando se visualizan en Outlook o en un cliente de correo web como Gmail o Hotmail. A continuación se muestra una captura de pantalla del mensaje al abrirlo con Gmail en un navegador Chrome.

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

El siguiente fragmento de código te muestra cómo usar un documento de Microsoft Word como cuerpo del mensaje y enviar un correo electrónico utilizando una instancia de la clase [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

```csharp
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-.NET

// Carga un documento de Word desde el disco y guárdalo en un stream como MHTML
Document wordDocument = new Document(folderPath + "invoice.docx");
MemoryStream mhtmlStream = new MemoryStream();
wordDocument.Save(mhtmlStream, SaveFormat.Mhtml);

// Carga el MHTML en un objeto MailMessage
mhtmlStream.Position = 0;
using (MailMessage message = MailMessage.Load(mhtmlStream, new MhtmlLoadOptions()))
{
    message.Subject = "Enviando Factura por Correo Electrónico";
    message.From = "sender@gmail.com";
    message.To = "recipient@gmail.com";

    // Guarda el mensaje en formato MSG en el disco
    message.Save(folderPath + "WordDocAsEmailBody_out.msg", SaveOptions.DefaultMsgUnicode);

    // Envía el mensaje de correo electrónico
    using (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "password"))
    {
        client.SecurityOptions = SecurityOptions.SSLExplicit;
        client.Send(message);
    }
}
```