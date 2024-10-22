---
title: "Cargando y Guardando Mensajes"
url: /es/net/loading-and-saving-message/
weight: 40
type: docs
---

# Cargando y Guardando Mensajes

## **Detección de Formatos de Archivos**

La API de Aspose.Email proporciona la capacidad de detectar el formato de archivo del archivo de mensaje proporcionado. El método [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) de la clase [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) se puede utilizar para lograr esto. Las siguientes clases y métodos se pueden utilizar para detectar el formato de archivo cargado.

- Clase [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/)
- Clase [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/)
- Clase [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) 
- Método [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat)
- Método [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1)

El siguiente fragmento de código le muestra cómo detectar formatos de archivo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}

## **Cargando un Mensaje con Opciones de Carga**

El siguiente fragmento de código le muestra cómo cargar un mensaje con opciones de carga.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}

### **Preservando el Formato del Mensaje Embebido Durante la Carga**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Cargando un Mensaje Preservando o Eliminando una Firma**

La preservación de la firma está soportada por defecto al cargar archivos EML. Para eliminar la firma, puede establecer la propiedad [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) en *true*.

El siguiente ejemplo de código muestra cómo eliminar una firma al cargar un mensaje:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```
### **Comprobando la Firma de Correos Electrónicos Seguros**

La clase [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) le permite comprobar la firma de objetos MailMessage seguros.

La clase [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) almacena los resultados de la verificación.

Los siguientes métodos de la clase [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) y un fragmento de código le permitirán procesar una firma:

- Método [SecureEmailManager.CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature).
- Método [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1).
- Método [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2).

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

## **Guardando y Convirtiendo Mensajes**

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta característica, el código en este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) para configuraciones adicionales al guardar [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) se pueden utilizar para guardar mensajes en otros formatos. El artículo muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
  
### **Cargar y Guardar un mensaje EML**

El siguiente fragmento de código le muestra cómo cargar un mensaje EML y guardarlo en el disco en el mismo formato.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

### **Cargar y Guardar un mensaje EML Preservando los Límites Originales**

El siguiente fragmento de código le muestra cómo cargar EML y guardar como EML preservando los límites originales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

### **Guardando como EML Preservando Archivos Adjuntos TNEF**

El siguiente fragmento de código muestra cómo guardar como EML preservando los archivos adjuntos TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Guardar EML como MSG**

El siguiente fragmento de código le muestra cómo cargar un mensaje EML y convertirlo a MSG utilizando la opción apropiada de [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

### **Guardando como MSG con Fechas Preservadas**

La clase [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) le permite guardar el mensaje fuente como un archivo de Mensaje de Outlook (MSG) preservando las fechas. El siguiente fragmento de código le muestra cómo guardar como MSG con fechas preservadas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Guardando MailMessage como MHTML**

Diferentes opciones de MHTML se pueden usar para obtener los resultados deseados. El siguiente fragmento de código le muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y convertirlo a MHTML con una fecha de mensaje en el sistema UTC.

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET

// Establecer opciones para la salida MHTML
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // guardar la fecha de un mensaje como fecha UTC

// Inicializar y cargar un archivo EML existente
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Convertir a MHTML con Configuraciones Opcionales**

La clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) hace posible escribir información adicional de correo electrónico en el MHTML de salida. Los siguientes campos adicionales pueden ser escritos:

- WriteHeader – escribir el encabezado del correo electrónico en el archivo de salida.
- WriteOutlineAttachments – escribir archivos adjuntos de esquema en el archivo de salida.
- WriteCompleteEmailAddress – escribir la dirección de correo electrónico completa en el archivo de salida.
- NoEncodeCharacters – no se debe utilizar codificación de transferencia de caracteres.
- HideExtraPrintHeader – ocultar el encabezado de impresión extra de la parte superior del archivo de salida.
- WriteCompleteToEmailAddress – escribir la dirección de correo electrónico completa del destinatario en el archivo de salida.
- WriteCompleteFromEmailAddress – escribir la dirección de correo electrónico completa del remitente en el archivo de salida.
- WriteCompleteCcEmailAddress – escribir las direcciones de correo electrónico completas de los destinatarios en copia en el archivo de salida.
- WriteCompleteBccEmailAddress – escribir la dirección de correo electrónico completa de los destinatarios en copia oculta en el archivo de salida.
- RenderCalendarEvent – escribir texto del evento de calendario en el archivo de salida.
- SkipByteOrderMarkInBody – escribir los bytes del Byte Order Mark (BOM) en el archivo de salida.
- RenderVCardInfo – escribir texto de VCard AlternativeView en el archivo de salida.
- DisplayAsOutlook – mostrar el encabezado From.
- RenderTaskFields – escribir campos específicos de tarea en el archivo de salida.
- None – No se especificó ninguna configuración.

El siguiente fragmento de código muestra cómo convertir archivos EML a MHTML con configuraciones opcionales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Renderizando Eventos de Calendario al Convertir a MHTML**

El [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) renderiza los eventos de Calendario a la salida MTHML. El siguiente fragmento de código le muestra cómo renderizar eventos de calendario al convertir a MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Exportando Correo Electrónico a MHT sin Imágenes Integradas**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Exportando Correo Electrónico a MHT con Zona Horaria Personalizada**

La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) proporciona la propiedad [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) para establecer una zona horaria personalizada al exportar a MHT. El siguiente fragmento de código le muestra cómo exportar correo electrónico a MHT con zona horaria personalizada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Cambiando la Fuente al Convertir a MHT**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

#### **Preservando el cuerpo RTF al convertir MSG a EML** 

La conversión de un archivo MSG a EML preservando el cuerpo RTF se puede hacer de dos maneras:

- utilizando la propiedad [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) de la clase [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/);

- utilizando la propiedad [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) de la clase [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/);

Ambas propiedades obtienen o establecen un valor que indica si mantener el cuerpo rtf en MailMessage.

Los siguientes fragmentos de código muestran cómo convertir un archivo MSG a EML y preservar el cuerpo RTF:

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

### **Exportando Correo Electrónico a EML**

El siguiente fragmento de código le muestra cómo exportar correos electrónicos a EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}

### **Guardando Mensaje como HTML**

La clase [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) le permite exportar el cuerpo del mensaje a HTML. El siguiente fragmento de código le muestra cómo guardar un mensaje como HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}


#### **Guardando como HTML sin Embebidos Recursos**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Guardando Mensaje como un archivo de plantilla de Outlook (.oft)**

El siguiente fragmento de código le muestra cómo guardar un mensaje como un archivo de plantilla de outlook (.oft).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}