---
title: "Cargando y Guardando Mensajes"
url: /es/java/loading-and-saving-message/
weight: 40
type: docs
---

# **Cargando y Guardando Mensajes de Correo Electrónico**

## **Detectar un Formato de Archivo**

La API de Aspose.Email proporciona la capacidad de detectar el formato de archivo del archivo de mensaje proporcionado. El método [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) de la clase [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) se puede usar para lograr esto. Las siguientes clases y métodos se pueden utilizar para detectar el formato de archivo cargado.

- Clase [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/)
- Clase [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/)
- Clase [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/)
- Método [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-)
- Método [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-)

El siguiente fragmento de código muestra cómo detectar formatos de archivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Cargar un Mensaje de Correo Electrónico**

Para cargar un mensaje con opciones de carga específicas, Aspose.Email proporciona la clase [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/) que se puede usar como sigue:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Preservar el Formato del Mensaje Integrado durante la Carga**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Guardar y Convertir Mensajes de Correo Electrónico**

Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta característica, el código en este artículo carga tres tipos de mensajes desde el disco y los guarda nuevamente en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) para configuraciones adicionales al guardar [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) se pueden utilizar para guardar mensajes en otros formatos. El artículo muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.

### **Cargar y Guardar un Mensaje de Correo Electrónico**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco en el mismo formato.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Cargar y Guardar un Mensaje de Correo Electrónico Preservando los Límites Originales**

El siguiente fragmento de código muestra cómo cargar EML y guardar como EML preservando los límites originales.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Guardar como EML Preservando los Archivos Adjuntos TNEF**

El siguiente fragmento de código muestra cómo guardar como EML preservando los archivos adjuntos TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Guardar EML como MSG**

El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo a MSG utilizando la opción adecuada de [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Guardar EML como MSG con Fechas Preservadas**

La clase [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) permite guardar el mensaje de origen como un archivo de mensaje de Outlook (MSG) preservando las fechas. El siguiente fragmento de código muestra cómo guardar como MSG con fechas preservadas.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Guardar EML como MHTML**

Se pueden utilizar diferentes opciones de MHTML para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y convertirlo a MHTML con una fecha de mensaje en el sistema UTC.

~~~Java
// Establecer opciones para la salida MHTML
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// guardar la fecha del mensaje como fecha UTC
saveOptions.setPreserveOriginalDate(false);

// Inicializar y cargar un archivo EML existente
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~

#### **Formatear Encabezados MHT Globalmente al Guardar desde EML**

Con Aspose.Email, puedes usar las opciones de formateo global para el encabezado Mht. Las opciones globales establecen el formato común de un encabezado Mht para todas las instancias de [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/). Esta función está diseñada para evitar establecer el formato para cada instancia de [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Utiliza los siguientes métodos de la clase [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) y el ejemplo de código a continuación para establecer el formato de un encabezado Mht:

- [setPageHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - PageHeaderFormat para instancias de HeadersFormattingOptions si DefaultPageHeaderFormat no está establecido.
- [setHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - HeaderFormat para instancias de HeadersFormattingOptions si DefaultHeaderFormat no está establecido.
- [setBeforeHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - BeforeHeadersFormat para instancias de HeadersFormattingOptions si BeforeHeadersFormat no está establecido.
- [setAfterHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - AfterHeadersFormat para instancias de HeadersFormattingOptions si AfterHeadersFormat no está establecido.

```java
// saveOptions1 y saveOptions2 tienen el mismo formato de encabezados mht
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Convertir EML a MHTML con Configuraciones Opcionales**

La clase [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) permite escribir información adicional del correo electrónico en la salida MHTML. Los siguientes campos adicionales pueden ser escritos:

- WriteHeader - escribir el encabezado del correo electrónico en el archivo de salida.
- WriteOutlineAttachments - escribir archivos adjuntos de esquema en el archivo de salida.
- WriteCompleteEmailAddress - escribir la dirección de correo electrónico completa en el archivo de salida.
- NoEncodeCharacters - no se debe usar codificación de caracteres de transferencia.
- HideExtraPrintHeader - ocultar el encabezado de impresión adicional en la parte superior del archivo de salida.
- WriteCompleteToEmailAddress - escribir la dirección de correo electrónico completa del destinatario en el archivo de salida.
- WriteCompleteFromEmailAddress - escribir la dirección de correo electrónico completa del remitente en el archivo de salida.
- WriteCompleteCcEmailAddress - escribir las direcciones de correo electrónico completas de cualquier destinatario en copia a ciegas en el archivo de salida.
- WriteCompleteBccEmailAddress - escribir la dirección de correo electrónico completa de cualquier destinatario en copia oculta en el archivo de salida.
- RenderCalendarEvent - escribir texto del evento del calendario en el archivo de salida.
- SkipByteOrderMarkInBody - escribir bytes de Marca de Orden de Byte(BOM) en el archivo de salida.
- RenderVCardInfo - escribir texto de VCard AlternativeView en el archivo de salida.
- DisplayAsOutlook - mostrar el encabezado De.
- RenderTaskFields - escribir campos de tarea específicos en el archivo de salida.
- None - No se especificó ninguna configuración.

El siguiente fragmento de código muestra cómo convertir archivos EML a MHTML con configuraciones opcionales.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Renderizar Eventos del Calendario al Convertir a MHTML**

El [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) renderiza los eventos del calendario a la salida MTHML. El siguiente fragmento de código muestra cómo renderizar eventos del calendario mientras se convierte a MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Exportar Correo Electrónico a MHT sin Imágenes Integradas**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Exportar Correo Electrónico a MHT con Zona Horaria Personalizada**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) proporciona la propiedad [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) para establecer la zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar un correo electrónico a MHT con zona horaria personalizada.

~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Establecer la compensación de la zona horaria en milisegundos
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~

### **Exportar Correo Electrónico a EML**

El siguiente fragmento de código muestra cómo exportar correos electrónicos a EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}

### **Guardar Correo Electrónico como HTML**

La clase [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) permite exportar el cuerpo del mensaje a HTML. El siguiente fragmento de código muestra cómo guardar un mensaje como HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Guardar Mensaje de Correo Electrónico como HTML con Ruta Relativa a Recursos**

Al exportar mensajes de correo electrónico al formato HTML, es posible elegir guardar los recursos de correo electrónico con rutas relativas. Esta función proporciona más flexibilidad en cómo se vinculan los recursos en el archivo HTML de salida, lo que facilita compartir y mostrar correos electrónicos guardados en diferentes sistemas. La propiedad [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) proporciona la capacidad de guardar recursos con rutas relativas. El valor predeterminado de la propiedad es falso (los recursos se guardan con rutas absolutas). Cuando se establece en verdadero, los recursos se guardan con rutas relativas. Los archivos HTML con rutas relativas son más portátiles y se pueden ver correctamente independientemente de la estructura de archivos del entorno de alojamiento. Puedes elegir entre rutas absolutas y relativas según los requisitos. Puedes definir rutas personalizadas para los recursos utilizando el evento [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/).

**Guardar con Ruta Relativa Predeterminada a Recursos**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
En este caso, los recursos se guardarán en la carpeta [nombre del archivo html].files, en la misma ruta que el archivo .html y el HTML hará referencia a los recursos a través de rutas relativas.

**Guardar con Ruta Absoluta a Recursos**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
Como en el primer caso, los recursos se guardarán en la carpeta [nombre del archivo html].files por defecto, pero el HTML hará referencia a los recursos utilizando rutas absolutas.

**Ruta Relativa Personalizada utilizando el Evento ResourceHtmlRenderingHandler**

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
            // Dado que UseRelativePathToResources = true, debes asignar una ruta relativa a la propiedad PathToResourceFile.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
Al utilizar el evento [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) evento, puedes establecer rutas personalizadas relativas o absolutas para los recursos. Al personalizar rutas con el controlador de eventos [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/), y dado que [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) está establecido en verdadero, debes asignar una ruta relativa a la propiedad [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) para garantizar una referencia correcta.

#### **Preservar Íconos Personalizados en un Mensaje al Convertir a HTML**

A veces, el mensaje contiene archivos adjuntos en línea, que se muestran como imágenes de íconos en el cuerpo del mensaje. Tales mensajes pueden crear problemas al convertirlos a HTML, ya que se pierden las imágenes de íconos. Esto se debe a que los íconos de los archivos adjuntos no se mantienen directamente en el mensaje.

El usuario de Aspose.Email puede personalizar los íconos para los archivos adjuntos al convertir el mensaje a HTML. Para eso, se usa el evento [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) para personalizar la representación de los archivos de recursos (como archivos adjuntos) al guardar un mensaje de correo electrónico como un archivo HTML. En el siguiente ejemplo de código, el controlador de eventos se utiliza para establecer dinámicamente la ruta a los archivos de recursos (íconos) según el tipo de contenido del archivo adjunto. Esto permite una representación personalizada de los recursos en la salida HTML según su tipo de archivo.

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

#### **Establecer Hora y Zona Horaria al Guardar EML como HTML**

Los usuarios de Aspose.Email pueden establecer los formatos de visualización de hora y zona horaria en [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). La clase [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) permite especificar opciones de formateo de encabezados al guardar MailMessage en formato Mhtml o Html. Los siguientes métodos de la clase [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) especifican los campos que se mostrarán en el archivo de salida:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Indica que el texto del evento del calendario debe escribirse en el mhtml de salida.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Indica que el texto de VCard AlternativeView debe escribirse en el html de salida.

El siguiente ejemplo de código muestra cómo establecer la hora y la zona horaria al guardar EML como HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Guardar como HTML sin Incrustar Recursos**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Guardar un Mensaje como un Archivo de Plantilla de Outlook (.oft)**

El siguiente fragmento de código muestra cómo guardar un mensaje como un archivo de plantilla de outlook (.oft).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}