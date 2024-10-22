---
title: "Guardar un correo electrónico como PDF"
url: /es/net/saving-an-email-as-pdf/
weight: 230
type: docs
---


Este artículo muestra cómo convertir un mensaje de correo electrónico a PDF utilizando Aspose.Email. Aspose.Email para .NET maneja protocolos de red y características de Microsoft Outlook, y no puede manejar la conversión directa a PDF. Para superar esto, los ejemplos en este artículo utilizan Aspose.Email para convertir el mensaje de correo electrónico al flujo MHTML y luego utilizan Aspose.Words para .NET para cargar el flujo MHTML y luego guardarlo como PDF. Un mensaje de correo electrónico también puede contener adjuntos. Dado que cada adjunto puede ser de diferentes tipos de medios, Aspose.Email ignora estos adjuntos al convertir a MHTML, es decir, solo las imágenes en línea en un mensaje formarán parte del MHTML y cualquier adjunto regular será ignorado.
## **Convertir mensaje de correo electrónico a PDF**
El siguiente código muestra cómo convertir mensajes de correo electrónico a PDF utilizando Aspose.Email en combinación con Aspose.Words para .NET. Esto implica los siguientes pasos:

1. Cargar el mensaje de correo electrónico usando [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage)
1. Guardar el mensaje de correo electrónico en MemoryStream como MHTML
1. Cargar el flujo usando Aspose.Words
1. Guardar el mensaje como PDF

El mensaje de correo electrónico fuente se puede ver como sigue:

![todo:image_alt_text](saving-an-email-as-pdf_1.png)

El PDF convertido es como se muestra en la siguiente imagen:

![todo:image_alt_text](saving-an-email-as-pdf_2.png)

El siguiente fragmento de código te muestra cómo convertir mensajes de correo electrónico a PDF.

```csharp
string dataDir = RunExamples.GetDataDir_KnowledgeBase();
MailMessage mailMsg = MailMessage.Load(dataDir + "message3.msg");
MemoryStream ms = new MemoryStream();
mailMsg.Save(ms, Aspose.Email.SaveOptions.DefaultMhtml);

// crear una instancia de LoadOptions y establecer el LoadFormat en Mhtml
var loadOptions = new Aspose.Words.Loading.LoadOptions();
loadOptions.LoadFormat = LoadFormat.Mhtml;

// crear una instancia de Document y cargar el MTHML desde MemoryStream
var document = new Aspose.Words.Document(ms, loadOptions);

// crear una instancia de HtmlSaveOptions y establecer el SaveFormat en Html
var saveOptions = new Aspose.Words.Saving.PdfSaveOptions();
document.Save(dataDir + "SaveEmailAsPDF_out.pdf", saveOptions);
```