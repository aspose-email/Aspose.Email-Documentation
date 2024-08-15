---
title: "Cargar y guardar el mensaje"
url: /es/python-net/loading-and-saving-message/
weight: 30
type: docs
---


## **Detección de formatos de archivo**
La API Aspose.Email ofrece la capacidad de detectar el formato de archivo del archivo de mensajes proporcionado. Para lograr esto, se puede usar el método DetectFileFormat de la clase FileFormatUtil. Se pueden usar las siguientes clases y métodos para detectar el formato de archivo cargado.

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Class [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Class [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Método detect_file_format (stream)
- Método detect_file_format (file_path)

El siguiente fragmento de código muestra cómo detectar formatos de archivo.

```py
from aspose.email.tools import FileFormatUtil

# Detect file format and get the detected load format
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("The message format is: " + str(info.file_format_type))
```
## **Carga de un mensaje con opciones de carga**
El siguiente fragmento de código muestra cómo cargar un mensaje con opciones de carga.

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions

# Load Eml, html, mhtml, msg, and dat files
mail_message = MailMessage.load(data_dir + "message.eml", EmlLoadOptions())
MailMessage.load(data_dir + "description.html", HtmlLoadOptions())
MailMessage.load(data_dir + "message.mhtml", MhtmlLoadOptions())
MailMessage.load(data_dir + "message.msg", MsgLoadOptions())

# Loading with custom options
eml_load_options = EmlLoadOptions()
eml_load_options.preferred_text_encoding = "utf-8"
eml_load_options.preserve_tnef_attachments = True

MailMessage.load(data_dir + "description.html", eml_load_options)

html_load_options = HtmlLoadOptions()
html_load_options.preferred_text_encoding = "utf-8"
html_load_options.should_add_plain_text_view = True
html_load_options.path_to_resources = data_dir

MailMessage.load(data_dir + "description.html", html_load_options)
```
### **Preservar el formato de los mensajes incrustados durante la carga**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Embedded message file format: " + str(file_format))
```
## **Guardar y convertir mensajes**
Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta función, el código de este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) para ajustes adicionales al guardar [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) se puede usar para guardar mensajes en otros formatos. En el artículo se muestra cómo usar estas clases para guardar un correo electrónico de ejemplo como:

- Formato EML.
- Mensaje de Outlook.
- Formato MHTML.
- Formato HTML.
### **Cargar EML y guardar como EML**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco con el mismo formato.

```py
from aspose.email import MailMessage, SaveOptions

# Initialize and Load an existing EML file by specifying the MessageFormat
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```
### **Cargar EML y guardar como EML conservando los límites originales**
El siguiente fragmento de código muestra cómo cargar EML y guardar como EML conservando los límites originales.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved original boundaries
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```
### **Guardar como EML Preservar los archivos adjuntos TNEF**
El siguiente fragmento de código muestra cómo guardar como EML conservando los archivos adjuntos TNEF.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Save as eml with preserved attachment
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```
### **Cargar EML, guardar en MSG**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo en MSG mediante la opción adecuada de [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save the Email message to disk in ASCII format and Unicode format
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```
### **Guardar como MSG con fechas preservadas**
The [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) La clase le permite guardar el mensaje de origen como un archivo de mensajes de Outlook (MSG) conservando las fechas. El siguiente fragmento de código muestra cómo guardar como MSG con fechas preservadas.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Save as msg with preserved dates
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```
### **Guardar MailMessage como MHTML**
Se pueden usar diferentes opciones de MHTML para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en[MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) y lo convierte a MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Initialize and Load an existing EML file by specifying the MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```
#### **Conversión a MHTML con ajustes opcionales**

The [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) La clase proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) permite escribir información de correo electrónico adicional en el MHTML de salida. Se pueden escribir los siguientes campos adicionales:

 - NINGUNO: no se especificó ninguna configuración específica.
 - WRITE_HEADER: indica que se debe escribir la información del encabezado.
 - WRITE_OUTLINE_ATTACHMENTS: indica que se deben escribir los anexos del esquema.
 - WRITE_COMPLETE_EMAIL_ADDRESS: indica que la dirección de correo electrónico completa debe escribirse en todos los encabezados de correo electrónico.
 - NO_ENCODE_CHARACTER: indica que no se debe utilizar ninguna codificación de transferencia de caracteres.
 - HIDE_EXTRA_PRINT_HEADER: indica que PageHeader no será visible.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS: indica que la dirección de correo electrónico completa debe escribirse en el encabezado «Para».
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS: indica que la dirección de correo electrónico completa debe escribirse en el encabezado «De».
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS: indica que la dirección de correo electrónico completa debe escribirse en el encabezado «Cc».
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS: indica que la dirección de correo electrónico completa debe escribirse en el encabezado «Bcc».
 - RENDER_CALENDAR_EVENT: indica que el texto del evento del calendario debe escribirse en el formato mhtml de salida.
 - SKIP_BYTE_ORDER_MARK_IN_BODY: indica que los bytes de la marca de orden de bytes (BOM) deben escribirse en el cuerpo.
 - RENDER_V_CARD_INFO: indica que el texto de vCard AlternativeView debe escribirse en el mhtml de salida.
 - DISPLAY_AS_OUTLOOK: indica que el encabezado Desde se mostrará como en Outlook.
 - RENDER_TASK_FIELDS: indica que los campos de tareas específicos deben escribirse en el mhtml de salida.

El siguiente fragmento de código muestra cómo convertir un archivo eml a MHTML con ajustes opcionales.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MailMessageSaveType, FileCompatibilityMode

# Load an existing EML file
eml = MailMessage.load(data_dir + "message.eml")

# Save as mht with header
mht_save_options = MhtSaveOptions()

# Specify formatting options required
# Here we are specifying to write header information to output without writing extra print header
# and the output headers should be displayed as the original headers in the message
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.HIDE_EXTRA_PRINT_HEADER | MhtFormatOptions.DISPLAY_AS_OUTLOOK

# Check the body encoding for validity.
mht_save_options.check_body_content_encoding = True

eml.save(data_dir + "outMessage_out.mht", mht_save_options)
```
#### **Representación de eventos del calendario durante la conversión a MHTML**
The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) renderiza los eventos del calendario en el MHTML de salida.
El siguiente fragmento de código muestra cómo representar los eventos del calendario durante la conversión a MHTML.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

file_name = "message.msg"

# Load the MSG file
msg = MailMessage.load(data_dir + file_name)

# Create MHT save options
options = MhtSaveOptions()
options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.RENDER_CALENDAR_EVENT

# Save the message as MHTML
msg.save(data_dir + "Meeting with Recurring Occurrences.mhtml", options)
```
#### **Exportación de correo electrónico a MHT sin imágenes en línea**

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

# Load the EML file
eml = MailMessage.load(data_dir + "message.eml")

# Create MHT save options
mht_save_options = MhtSaveOptions()
mht_save_options.skip_inline_images = True

# Save the message as MHTML without inline images
eml.save(data_dir + "EmlToMhtmlWithoutInlineImages_out.mht", mht_save_options)
```
#### **Exportación de correo electrónico a MHT con zona horaria personalizada**
[MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) La clase proporciona la propiedad TimeZoneOffset para establecer una zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar un correo electrónico a MHT con una zona horaria personalizada.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode
from datetime import timedelta

# Load the EML file
eml = MailMessage.load(data_dir + "message.eml")

# Set the local time for message date
eml.time_zone_offset = timedelta(hours=-8)

# The dates will be rendered by the local system time zone
mht_save_options = MhtSaveOptions()
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER
eml.save(data_dir + "ExportEmailToMHTWithCustomTimezone_out.mhtml", mht_save_options)
```
### **Exportación de correo electrónico a EML**
El siguiente fragmento de código muestra cómo exportar el correo electrónico a eml.

```py
from aspose.email import MailMessage, SaveOptions

# Load the EML file
msg = MailMessage.load(data_dir + "message.eml")

# Save the Email message as EML
msg.save(data_dir + "ExporttoEml_out.eml", SaveOptions.default_eml)
```
### **Guardar mensaje como HTML**
The [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) La clase le permite exportar el cuerpo del mensaje a HTML con la opción de guardar los recursos incrustados. El siguiente fragmento de código muestra cómo guardar un mensaje como HTML cuando el valor predeterminado de embed_resources es true.

```py
from aspose.email import MailMessage, SaveOptions, HtmlSaveOptions, HtmlFormatOptions

# Load the EML file
message = MailMessage.load(data_dir + "message.eml")

# Save the Email message as HTML
message.save(data_dir + "SaveAsHTML_out.html", SaveOptions.default_html)

# OR

eml = MailMessage.load(data_dir + "message.eml")
options = HtmlSaveOptions()
options.embed_resources = False
options.html_format_options = (
    HtmlFormatOptions.WRITE_HEADER
    | HtmlFormatOptions.WRITE_COMPLETE_EMAIL_ADDRESS
)  # save the message headers to output HTML using the formatting options
eml.save(data_dir + "SaveAsHTML1_out.html", options)
```

### **Guardar el mensaje como archivo de plantilla de Outlook (.oft)**
El siguiente fragmento de código muestra cómo guardar el mensaje como archivo de plantilla de Outlook (.oft).

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "template subject", "Template body")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```
