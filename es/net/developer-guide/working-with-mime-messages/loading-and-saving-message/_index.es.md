---
title: "Cargar y guardar el mensaje"
url: /es/net/loading-and-saving-message/
weight: 40
type: docs
---

# Carga y almacenamiento de mensajes

## **Detección de formatos de archivo**

La API Aspose.Email ofrece la capacidad de detectar el formato de archivo del archivo de mensajes proporcionado. El [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) método de [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) la clase se puede utilizar para lograr esto. Se pueden usar las siguientes clases y métodos para detectar el formato de archivo cargado.

- [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) Class
- [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat) Method
- [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1) Method

El siguiente fragmento de código muestra cómo detectar formatos de archivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}

## **Carga de un mensaje con opciones de carga**

El siguiente fragmento de código muestra cómo cargar un mensaje con opciones de carga.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}

### **Preservar el formato de los mensajes incrustados durante la carga**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Cargar un mensaje Conservar o eliminar una firma**

La conservación de firmas se admite de forma predeterminada al cargar archivos EML. Para eliminar la firma, puede configurar el [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) propiedad a *true*.

El ejemplo de código que aparece a continuación muestra cómo eliminar una firma al cargar un mensaje:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```
### **Comprobar la firma de correos electrónicos seguros**

The [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) La clase le permite comprobar la firma de los objetos MailMessage seguros.

The [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) La clase almacena los resultados de la comprobación.

Los siguientes métodos del [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) una clase y un fragmento de código le permitirán procesar una firma:

- [SecureEmailManager.checkSignature (mensaje de correo electrónico)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) method.
- [SecureEmailManager.CheckSignature (mensaje de mensaje de correo, certificado X509 Certificate2 para descifrar)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) method.
- [SecureEmailManager.CheckSignature (mensaje de mensaje de correo, certificado X509 Certificate2 para desencriptar, almacén X509)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2) method.

```cs
var eml = MailMessage.Load(fileName);
var result = new SecureEmailManager().CheckSignature(eml);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MailMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```


## **Guardar y convertir mensajes**

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, el código de este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) para ajustes adicionales al guardar [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) se puede usar para guardar mensajes en otros formatos. En el artículo se muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Mensaje de Outlook.
- Formato MHTML.
- Formato HTML.
 
### **Cargar y guardar un mensaje EML**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco con el mismo formato.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

### **Cargar y guardar un mensaje EML conservando los límites originales**

El siguiente fragmento de código muestra cómo cargar EML y guardar como EML conservando los límites originales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

### **Guardar como EML Preservar los archivos adjuntos TNEF**

El siguiente fragmento de código muestra cómo guardar como EML conservando los archivos adjuntos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Guardar EML como MSG**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo en MSG mediante la opción adecuada de [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

### **Guardar como MSG con fechas preservadas**

The [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) La clase le permite guardar el mensaje de origen como un archivo de mensajes de Outlook (MSG) conservando las fechas. El siguiente fragmento de código muestra cómo guardar como MSG con fechas preservadas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Guardar MailMessage como MHTML**

Se pueden usar diferentes opciones de MHTML para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y conviértelo a MHTML con la fecha del mensaje en el sistema UTC.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // save a message date as UTC date

// Initialize and load an existing EML file
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Conversión a MHTML con ajustes opcionales**

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) La clase proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) permite escribir información de correo electrónico adicional en el MHTML de salida. Se pueden escribir los siguientes campos adicionales:

- writeHeader: escribe el encabezado del correo electrónico en el archivo de salida.
- WriteOutlineAttachments: escribe archivos adjuntos de esquema en el archivo de salida.
- writeCompleteEmailAddress: escribe la dirección de correo electrónico completa en el archivo de salida.
- noEncodeCharacters: no se debe utilizar ninguna codificación de transferencia de caracteres.
- hideExtraPrintHeader: oculta el encabezado de impresión adicional en la parte superior del archivo de salida.
- WriteCompleteToEmailAddress: escribe la dirección de correo electrónico completa del destinatario en el archivo de salida.
- WriteCompleteFromEmailAddress: escribe la dirección de correo electrónico completa del remitente en el archivo de salida.
- WriteCompleteCCEMailAddress: escribe las direcciones de correo electrónico completas de todos los destinatarios copiados al carbono en el archivo de salida.
- WriteCompleteBccEmailAddress: escriba la dirección de correo electrónico completa de cualquier destinatario copiado a ciegas en carbono en el archivo de salida.
- renderCalendarEvent: escribe el texto del evento del calendario en el archivo de salida.
- skipByteOrderMarkinBody: escribe bytes de Byte Order Mark (BOM) en el archivo de salida.
- RenderVCardInfo: escribe texto desde vCard AlternativeView en el archivo de salida.
- DisplayAsOutlook: muestra el encabezado Desde.
- RenderTaskFields: escribe campos de tareas específicos en el archivo de salida.
- Ninguno: no se especificó ningún ajuste.

El siguiente fragmento de código muestra cómo convertir archivos EML a MHTML con ajustes opcionales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Representación de eventos del calendario durante la conversión a MHTML**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) renderiza los eventos del calendario en el MHTML de salida. El siguiente fragmento de código muestra cómo representar los eventos del calendario durante la conversión a MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Exportación de correo electrónico a MHT sin imágenes en línea**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Exportación de correo electrónico a MHT con zona horaria personalizada**

[MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) la clase proporciona la [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) propiedad para establecer una zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar el correo electrónico a MHT con una zona horaria personalizada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Cambiar la fuente durante la conversión a MHT**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

#### **Preservar el cuerpo del RTF al convertir MSG en EML**

La conversión de un archivo MSG a EML conservando el cuerpo RTF se puede realizar de dos maneras:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) propiedad del [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/) class;

- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) propiedad del [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/) class;

Ambas propiedades obtienen o establecen un valor que indica si se debe mantener el cuerpo rtf en MailMessage.

Los siguientes fragmentos de código muestran cómo convertir un archivo MSG a EML y conservar el cuerpo RTF:

```cs
var loadOptions = new MsgLoadOptions
{
    PreserveRtfContent = true
};

var eml = MailMessage.Load("my.msg", loadOptions);
```

```cs
var conversionOptions = new MailConversionOptions
{
    PreserveRtfContent = true
};

var msg = MapiMessage.Load("my.msg");

var eml = msg.ToMailMessage(conversionOptions);
```

### **Exportación de correo electrónico a EML**

El siguiente fragmento de código muestra cómo exportar correos electrónicos a EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}

### **Guardar mensaje como HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) La clase le permite exportar el cuerpo del mensaje a HTML. El siguiente fragmento de código muestra cómo guardar un mensaje como HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}


#### **Guardar como HTML sin incrustar recursos**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Guardar el mensaje como archivo de plantilla de Outlook (.oft)**

El siguiente fragmento de código muestra cómo guardar un mensaje como un archivo de plantilla de Outlook (.oft).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}
