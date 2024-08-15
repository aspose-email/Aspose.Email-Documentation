---
title: "Conversión del archivo de mensajes de Outlook (MSG) a una imagen TIFF"
url: /es/net/converting-outlook-message-file-msg-to-tiff-image/
weight: 130
type: docs
---


En este artículo, le mostramos cómo convertir un archivo MSG de Outlook en una imagen TIFF.

1. Primero, lee un archivo MSG y conviértelo a formato MHTML con Aspose.Email for.NET. Usa el [Aspose.Email.MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) clase para cargar el archivo de mensajes.
1. Tras cargar el archivo, llame al [MailMessage.Save()](https://apireference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) método y guárdalo para transmitirlo en formato MHTML.
1. Utilice Aspose.Words para.NET para convertir la secuencia MHTML a TIFF. Utilice el [Aspose.Words.Document](https://apireference.aspose.com/net/words/aspose.words/document) clase para cargar la secuencia MHTML.
1. Por último, llame al [Document.Save()](https://apireference.aspose.com/net/words/aspose.words/document/methods/save/index) método para guardar el documento MHTML en TIFF.

Si el documento contiene varias páginas, se genera un archivo TIFF de varias páginas. Los fragmentos de código siguientes muestran cómo convertir un archivo de mensajes de Outlook (MSG) en una imagen TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}
