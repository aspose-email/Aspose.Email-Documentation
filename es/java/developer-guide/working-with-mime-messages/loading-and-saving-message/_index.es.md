---
title: "Carga y almacenamiento de mensajes"
url: /es/java/loading-and-saving-message/
weight: 40
type: docs
---

# **Carga y almacenamiento de mensajes de correo electrónico**

## **Detectar un formato de archivo**

La API Aspose.Email ofrece la capacidad de detectar el formato de archivo del archivo de mensajes proporcionado. El [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) método del [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) la clase se puede utilizar para lograr esto. Se pueden usar las siguientes clases y métodos para detectar el formato de archivo cargado.

- [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/) Class
- [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) Method
- [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-) Method

El siguiente fragmento de código muestra cómo detectar formatos de archivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Cargar un mensaje de correo electrónico**

Para cargar un mensaje con opciones de carga específicas, Aspose.Email proporciona [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/) clase que se puede usar de la siguiente manera:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Conservar el formato del mensaje incrustado durante la carga**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Guardar y convertir mensajes de correo electrónico**

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, el código de este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) para ajustes adicionales al guardar [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) se puede usar para guardar mensajes en otros formatos. En el artículo se muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Mensaje de Outlook.
- Formato MHTML.
- Formato HTML.
 
### **Cargar y guardar un mensaje de correo electrónico**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco con el mismo formato.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Cargar y guardar un mensaje de correo electrónico conservando los límites originales**

El siguiente fragmento de código muestra cómo cargar EML y guardar como EML conservando los límites originales.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Guardar como EML Preservar los archivos adjuntos TNEF**

El siguiente fragmento de código muestra cómo guardar como EML conservando los archivos adjuntos TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Guardar EML en MSG**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo en MSG mediante la opción adecuada de [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Guarde EML en MSG con fechas preservadas**

The [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) La clase le permite guardar el mensaje de origen como un archivo de mensajes de Outlook (MSG) conservando las fechas. El siguiente fragmento de código muestra cómo guardar como MSG con fechas preservadas.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Guardar EML como MHTML**

Se pueden usar diferentes opciones de MHTML para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y conviértelo a MHTML con la fecha del mensaje en el sistema UTC.

~~~Java
// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// save a message date as UTC date
saveOptions.setPreserveOriginalDate(false);

// Initialize and load an existing EML file
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~
#### **Formatee los encabezados MHT globalmente al guardarlos desde EML**

Con Aspose.Email, puede usar las opciones de formato global para el encabezado Mht. Las opciones globales establecen el formato común de un encabezado Mht para todos [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) instancias. Esta función está diseñada para evitar establecer el formato de cada instancia de [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Utilice los siguientes métodos de [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) clase y el siguiente ejemplo de código para establecer el formato de un encabezado Mht:

- [setPageHeaderFormat (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - PageHeaderFormat para instancias de HeadersFormattingOptions si DefaultPageHeaderFormat no está establecido.
- [setHeaderFormat (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - HeaderFormat para instancias de HeadersFormattingOptions si DefaulHeaderFormat no está establecido.
- [setBeforeHeadersFormat (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - BeforeHeadersFormat para instancias de HeadersFormattingOptions si BeforeHeadersFormat no está establecido.
- [setAfterHeadersFormat (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - AfterHeadersFormat para instancias de HeadersFormattingOptions si AfterHeadersFormat no está configurado.

```java
// saveOptions1 and saveOptions2 have the same mht header formatting
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Convierta EML a MHTML con configuraciones opcionales**

The [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) La clase proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) permite escribir información de correo electrónico adicional en el MHTML de salida. Se pueden escribir los siguientes campos adicionales:

- writeHeader: escribe el encabezado del correo electrónico en el archivo de salida.
- WriteOutlineAttachments: escribe archivos adjuntos de esquema en el archivo de salida.
- WriteCompleteEmailAddress: escribe la dirección de correo electrónico completa en el archivo de salida.
- noEncodeCharacters: no se debe utilizar ninguna codificación de transferencia de caracteres.
- hideExtraPrintHeader: oculta el encabezado de impresión adicional en la parte superior del archivo de salida.
- WriteCompleteToEmailAddress: escribe la dirección de correo electrónico completa del destinatario en el archivo de salida.
- WriteCompleteFromEmailAddress: escribe la dirección de correo electrónico completa del remitente en el archivo de salida.
- WriteCompleteCCEMailAddress: escribe las direcciones de correo electrónico completas de cualquier destinatario copiado al carbono en el archivo de salida.
- WriteCompleteBccEmailAddress: escribe la dirección de correo electrónico completa de cualquier destinatario copiado a ciegas en el archivo de salida.
- renderCalendarEvent: escribe texto del evento del calendario en el archivo de salida.
- skipByteOrderMarkinBody: escribe bytes de Byte Order Mark (BOM) en el archivo de salida.
- RenderVCardInfo: escribe texto desde vCard AlternativeView en el archivo de salida.
- DisplayAsOutlook: muestra desde el encabezado.
- RenderTaskFields: escribe campos de tareas específicos en el archivo de salida.
- Ninguno: no se especificó ningún ajuste.

El siguiente fragmento de código muestra cómo convertir archivos EML a MHTML con ajustes opcionales.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Renderice los eventos del calendario durante la conversión a MHTML**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) representa los eventos del calendario en el MHTML de salida. El siguiente fragmento de código muestra cómo representar los eventos del calendario durante la conversión a MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Exportación de correo electrónico a MHT sin imágenes en línea**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Exportar correo electrónico a MHT con zona horaria personalizada**

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) la clase proporciona la [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) propiedad para establecer una zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar el correo electrónico a MHT con una zona horaria personalizada.

~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Set the timezone offset in milliseconds
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~

### **Exportación de correo electrónico a EML**

El siguiente fragmento de código muestra cómo exportar correos electrónicos a EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}

### **Guardar correo electrónico como HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) La clase le permite exportar el cuerpo del mensaje a HTML. El siguiente fragmento de código muestra cómo guardar un mensaje como HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Guardar el mensaje de correo electrónico como HTML con la ruta relativa a los recursos**

Al exportar mensajes de correo electrónico a formato HTML, es posible elegir guardar los recursos de correo electrónico con rutas relativas. Esta función proporciona más flexibilidad a la hora de vincular los recursos en el archivo HTML de salida, lo que facilita compartir y mostrar los correos electrónicos guardados en diferentes sistemas. El [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) la propiedad brinda la capacidad de ahorrar recursos con rutas relativas. El valor predeterminado de la propiedad es falso (los recursos se guardan con rutas absolutas). Cuando se establece en verdadero, los recursos se guardan con rutas relativas. Los archivos HTML con rutas relativas son más portátiles y se pueden ver correctamente independientemente de la estructura de archivos del entorno de alojamiento. Puede elegir entre rutas absolutas y relativas en función de los requisitos. Puede definir rutas personalizadas para los recursos mediante el [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) event.

**Guardar con la ruta relativa predeterminada a los recursos**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
En este caso, los recursos se guardarán en la carpeta [nombre del archivo html] .files, en la misma ruta que el archivo.html, y el HTML hará referencia a los recursos mediante rutas relativas.

**Ahorre con Absolute Path to Resources**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
Como en el primer caso, los recursos se guardarán en la carpeta [nombre del archivo html] .files de forma predeterminada, pero el HTML hará referencia a los recursos mediante rutas absolutas.

**Ruta relativa personalizada mediante el evento ResourceHTMLRenderingHandler**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

htmlSaveOptions.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {
    @Override
    public void invoke(Object sender, ResourceHtmlRenderingEventArgs args) {
        if (sender instanceof AttachmentBase) {
            AttachmentBase attachment = (AttachmentBase) sender;
            // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
Mediante el uso del [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) evento, puede establecer rutas absolutas o relativas personalizadas para los recursos. Al personalizar las rutas con el [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) controlador de eventos, y desde [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) está establecido en verdadero, debe asignar una ruta relativa al [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) propiedad para garantizar una referencia correcta.

#### **Conservar los iconos personalizados en un mensaje durante la conversión a HTML**

A veces, el mensaje contiene archivos adjuntos en línea, que se muestran como imágenes de iconos en el cuerpo del mensaje. Estos mensajes pueden crear problemas al convertirlos a HTML, ya que las imágenes de los iconos se pierden. Esto se debe a que los iconos de los archivos adjuntos no se guardan directamente en el mensaje.

El usuario de Aspose.Email puede personalizar los iconos de los archivos adjuntos al convertir el mensaje a HTML. Para ello, el [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) El evento se usa para personalizar la representación de los archivos de recursos (como los archivos adjuntos) al guardar un mensaje de correo electrónico como archivo HTML. En el ejemplo de código que aparece a continuación, el controlador de eventos se usa para establecer dinámicamente la ruta a los archivos de recursos (iconos) en función del tipo de contenido del adjunto. Esto permite la representación personalizada de los recursos en la salida HTML en función de su tipo de archivo.

```java

 HtmlSaveOptions options = new HtmlSaveOptions();

options.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {

   @Override

   public void invoke(Object sender, ResourceHtmlRenderingEventArgs e) {

        AttachmentBase attachment = (AttachmentBase) sender;

        e.setCaption(attachment.getContentType().getName());

       if (attachment.getContentType().getName().endsWith(".pdf")) {

            e.setPathToResourceFile("pdf_icon.png");

       } else if (attachment.getContentType().getName().endsWith(".docx")) {

            e.setPathToResourceFile("word_icon.jpg");

       } else if (attachment.getContentType().getName().endsWith(".jpg")) {

            e.setPathToResourceFile("jpeg_icon.png");

       } else {

            e.setPathToResourceFile("not_found_icon.png");

       }

   }

});

options.setResourceRenderingMode(ResourceRenderingMode.SubstituteFromFile);

String fileName = "message.msg";

MailMessage mailMessage = MailMessage.load(fileName);

mailMessage.save("fileName.html", options);

```

#### **Establezca la hora y la zona horaria al guardar EML como HTML**

Los usuarios de Aspose.Email pueden configurar los formatos de visualización de la hora y la zona horaria en [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). El [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) La clase permite especificar las opciones de formato de los encabezados al guardar MailMessage en formato Mhtml o Html. Los siguientes métodos del [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) clase especifica los campos que se mostrarán en el archivo de salida:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Indica que el texto del evento del calendario debe escribirse en la salida mhtml.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Indica que el texto de vCard AlternativeView debe escribirse en el código HTML de salida.

El siguiente ejemplo de código muestra cómo establecer la hora y la zona horaria al guardar EML en HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Guardar como HTML sin incrustar recursos**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Guardar un mensaje como un archivo de plantilla de Outlook (.oft)**

El siguiente fragmento de código muestra cómo guardar un mensaje como un archivo de plantilla de Outlook (.oft).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}
