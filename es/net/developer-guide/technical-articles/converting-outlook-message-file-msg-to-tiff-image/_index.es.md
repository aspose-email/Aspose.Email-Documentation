---
title: "Conversión de archivo de mensaje de Outlook (MSG) a imagen TIFF"
url: /es/net/converting-outlook-message-file-msg-to-tiff-image/
weight: 130
type: docs
---


En este artículo, te mostramos cómo convertir un archivo MSG de Outlook a una imagen TIFF.

1. Primero, lee un archivo MSG y conviértelo al formato MHTML con Aspose.Email para .NET. Usa la clase [Aspose.Email.MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) para cargar el archivo de mensaje.
1. Después de cargar el archivo, llama al método [MailMessage.Save()](https://apireference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) y guárdalo en un flujo en formato MHTML.
1. Usa Aspose.Words para .NET para convertir el flujo MHTML a TIFF. Usa la clase [Aspose.Words.Document](https://apireference.aspose.com/net/words/aspose.words/document) para cargar el flujo MHTML.
1. Finalmente, llama al método [Document.Save()](https://apireference.aspose.com/net/words/aspose.words/document/methods/save/index) para guardar el documento MHTML en TIFF.

Si el documento contiene múltiples páginas, se genera un archivo TIFF de varias páginas. Los fragmentos de código a continuación muestran cómo convertir un archivo de mensaje de Outlook (MSG) a una imagen TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}