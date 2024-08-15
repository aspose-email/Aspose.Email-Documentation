---
title: "Guardar un correo electrónico como PDF"
url: /es/net/saving-an-email-as-pdf/
weight: 230
type: docs
---


Este artículo muestra cómo convertir un mensaje de correo electrónico a PDF con Aspose.Email. Aspose.Email para .NET se ocupa de los protocolos de red y las funciones de Microsoft Outlook, y no puede gestionar la conversión directa a PDF. Para solucionar este problema, en los ejemplos de este artículo se utiliza Aspose.Email para convertir el mensaje de correo electrónico en la secuencia MHTML y, a continuación, se utiliza Aspose.Words para.NET para cargar la secuencia MHTML y, a continuación, guardarla como PDF. Un mensaje de correo electrónico también puede contener archivos adjuntos. Como cada archivo adjunto puede ser de diferentes tipos de medios, Aspose.Email ignora estos archivos adjuntos al convertir a MHTML, es decir, solo las imágenes en línea de un mensaje formarán parte de MHTML y se ignorarán los archivos adjuntos normales.
## **Conversión de un mensaje de correo electrónico a PDF**
El siguiente código muestra la conversión de mensajes de correo electrónico a PDF mediante Aspose.Email en combinación con Aspose.Words for.NET. Esto implica los siguientes pasos:

1. Cargue el mensaje de correo electrónico usando [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage)
1. Guarde el mensaje de correo electrónico en MemoryStream como MHTML
1. Carga la transmisión con Aspose.Words
1. Guarda el mensaje como PDF

El mensaje de correo electrónico de origen se puede ver de la siguiente manera:

![todo:image_alt_text](saving-an-email-as-pdf_1.png)

El PDF convertido es el que se muestra en la siguiente imagen:

![todo:image_alt_text](saving-an-email-as-pdf_2.png)

El siguiente fragmento de código muestra cómo convertir mensajes de correo electrónico a PDF.

```csharp
string dataDir = RunExamples.GetDataDir_KnowledgeBase();
MailMessage mailMsg = MailMessage.Load(dataDir + "message3.msg");
MemoryStream ms = new MemoryStream();
mailMsg.Save(ms, Aspose.Email.SaveOptions.DefaultMhtml);

// create an instance of LoadOptions and set the LoadFormat to Mhtml
var loadOptions = new Aspose.Words.Loading.LoadOptions();
loadOptions.LoadFormat = LoadFormat.Mhtml;

// create an instance of Document and load the MTHML from MemoryStream
var document = new Aspose.Words.Document(ms, loadOptions);

// create an instance of HtmlSaveOptions and set the SaveFormat to Html
var saveOptions = new Aspose.Words.Saving.PdfSaveOptions();
document.Save(dataDir + "SaveEmailAsPDF_out.pdf", saveOptions);
```
