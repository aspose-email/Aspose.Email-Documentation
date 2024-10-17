---
title: "Cargando y Guardando Mensaje"
url: /es/python-net/loading-and-saving-message/
weight: 30
type: docs
---

## **Detectando Formatos de Archivo**
Aspose.Email API proporciona la capacidad de detectar el formato de archivo del mensaje proporcionado. El método DetectFileFormat de la clase FileFormatUtil se puede usar para lograr esto. Las siguientes clases y métodos se pueden usar para detectar el formato de archivo cargado.

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Class [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Class [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Method detect_file_format(stream)
- Method detect_file_format(file_path)

El siguiente fragmento de código muestra cómo detectar formatos de archivo.

```py
from aspose.email.tools import FileFormatUtil

# Detectar formato de archivo y obtener el formato de carga detectado
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("El formato del mensaje es: " + str(info.file_format_type))
```
## **Cargando un Mensaje con Opciones de Carga**
El siguiente fragmento de código muestra cómo cargar un mensaje con opciones de carga.

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions

# Cargar archivos Eml, html, mhtml, msg y dat
mail_message = MailMessage.load(data_dir + "message.eml", EmlLoadOptions())
MailMessage.load(data_dir + "description.html", HtmlLoadOptions())
MailMessage.load(data_dir + "message.mhtml", MhtmlLoadOptions())
MailMessage.load(data_dir + "message.msg", MsgLoadOptions())

# Carga con opciones personalizadas
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
### **Preservando el Formato del Mensaje Embebido durante la Carga**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Formato de archivo del mensaje embebido: " + str(file_format))
```
## **Guardando y Convirtiendo Mensajes**
Aspose.Email facilita la conversión de cualquier tipo de mensaje a otro formato. Para demostrar esta característica, el código en este artículo carga tres tipos de mensajes desde el disco y los guarda en otros formatos. La clase base [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) y las clases [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) para configuraciones adicionales al guardar [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) se pueden usar para guardar mensajes en otros formatos. El artículo muestra cómo usar estas clases para guardar un correo electrónico de muestra como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
### **Cargando EML y Guardando como EML**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y guardarlo en el disco en el mismo formato.

```py
from aspose.email import MailMessage, SaveOptions

# Inicializar y cargar un archivo EML existente especificando el MessageFormat
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```
### **Cargando EML y Guardando como EML Preservando los Límites Originales**
El siguiente fragmento de código muestra cómo cargar EML y guardar como EML preservando los límites originales.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Guardar como eml con límites originales preservados
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```
### **Guardando como EML Preservando Adjuntos TNEF**
El siguiente fragmento de código muestra cómo guardar como EML preservando adjuntos TNEF.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Guardar como eml con adjunto preservado
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```
### **Cargando EML, Guardando a MSG**
El siguiente fragmento de código muestra cómo cargar un mensaje EML y convertirlo a MSG utilizando la opción adecuada de [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar y cargar un archivo EML existente especificando el MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Guardar el mensaje de correo electrónico en disco en formato ASCII y formato Unicode
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```
### **Guardando como MSG con Fechas Preservadas**
La clase [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) permite guardar el mensaje de origen como un archivo de Mensaje de Outlook (MSG) preservando las fechas. El siguiente fragmento de código muestra cómo guardar como MSG con fechas preservadas.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar y cargar un archivo EML existente especificando el MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Guardar como msg con fechas preservadas
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```
### **Guardando MailMessage como MHTML**
Diferentes opciones de MHTML se pueden usar para obtener los resultados deseados. El siguiente fragmento de código muestra cómo cargar un mensaje EML en [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) y convertirlo a MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar y cargar un archivo EML existente especificando el MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```
#### **Convertir a MHTML con Configuraciones Opcionales**

La clase [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) proporciona opciones adicionales para guardar mensajes de correo electrónico en formato MHTML. El enumerador [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) hace posible escribir información adicional del correo electrónico en el MHTML de salida. Los siguientes campos adicionales se pueden escribir:

 - NONE - No se especifican configuraciones específicas.
 - WRITE_HEADER - Indica que la información de encabezado debe escribirse.
 - WRITE_OUTLINE_ATTACHMENTS - Indica que los adjuntos de esquema deben escribirse.
 - WRITE_COMPLETE_EMAIL_ADDRESS - Indica que la dirección de correo electrónico completa debe escribirse en todos los encabezados de correo electrónico.
 - NO_ENCODE_CHARACTERS - Indica que no se debe utilizar codificación de caracteres para la transferencia.
 - HIDE_EXTRA_PRINT_HEADER - Indica que el PageHeader será invisible.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS - Indica que la dirección de correo electrónico completa debe escribirse en el encabezado 'To'.
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS - Indica que la dirección de correo electrónico completa debe escribirse en el encabezado 'From'.
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS - Indica que la dirección de correo electrónico completa debe escribirse en el encabezado 'Cc'.
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS - Indica que la dirección de correo electrónico completa debe escribirse en el encabezado 'Bcc'.
 - RENDER_CALENDAR_EVENT - Indica que el texto del evento del calendario debe escribirse en el MHTML de salida.
 - SKIP_BYTE_ORDER_MARK_IN_BODY - Indica que los bytes de Byte Order Mark (BOM) deben escribirse en el cuerpo.
 - RENDER_V_CARD_INFO - Indica que el texto de la VCard AlternativeView debe escribirse en el MHTML de salida.
 - DISPLAY_AS_OUTLOOK - Indica que el encabezado From se mostrará como en Outlook.
 - RENDER_TASK_FIELDS - Indica que los campos de tarea específicos deben escribirse en el MHTML de salida.

El siguiente fragmento de código muestra cómo convertir un archivo eml a MHTML con configuraciones opcionales.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MailMessageSaveType, FileCompatibilityMode

# Cargar un archivo EML existente
eml = MailMessage.load(data_dir + "message.eml")

# Guardar como mht con encabezado
mht_save_options = MhtSaveOptions()

# Especificar opciones de formato requeridas
# Aquí estamos especificando escribir información de encabezado en la salida sin escribir un encabezado de impresión adicional
# y los encabezados de salida deben mostrarse como los encabezados originales en el mensaje
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.HIDE_EXTRA_PRINT_HEADER | MhtFormatOptions.DISPLAY_AS_OUTLOOK

# Verificar la codificación del cuerpo por validez.
mht_save_options.check_body_content_encoding = True

eml.save(data_dir + "outMessage_out.mht", mht_save_options)
```
#### **Renderizando Eventos de Calendario al Convertir a MHTML**
El [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) renderiza los eventos de Calendario al MTHML de salida.
El siguiente fragmento de código muestra cómo renderizar eventos de calendario mientras se convierte a MHTML.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

file_name = "message.msg"

# Cargar el archivo MSG
msg = MailMessage.load(data_dir + file_name)

# Crear opciones de guardado MHT
options = MhtSaveOptions()
options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.RENDER_CALENDAR_EVENT

# Guardar el mensaje como MHTML
msg.save(data_dir + "Meeting with Recurring Occurrences.mhtml", options)
```
#### **Exportando Correo Electrónico a MHT sin Imágenes Integradas**

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

# Cargar el archivo EML
eml = MailMessage.load(data_dir + "message.eml")

# Crear opciones de guardado MHT
mht_save_options = MhtSaveOptions()
mht_save_options.skip_inline_images = True

# Guardar el mensaje como MHTML sin imágenes integradas
eml.save(data_dir + "EmlToMhtmlWithoutInlineImages_out.mht", mht_save_options)
```
#### **Exportando Correo Electrónico a MHT con Zona Horaria Personalizada**
La clase [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) proporciona la propiedad TimeZoneOffset para establecer la zona horaria personalizada al exportar a MHT. El siguiente fragmento de código muestra cómo exportar un correo electrónico a MHT con una zona horaria personalizada.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode
from datetime import timedelta

# Cargar el archivo EML
eml = MailMessage.load(data_dir + "message.eml")

# Establecer la hora local para la fecha del mensaje
eml.time_zone_offset = timedelta(hours=-8)

# Las fechas serán renderizadas por la zona horaria del sistema local
mht_save_options = MhtSaveOptions()
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER
eml.save(data_dir + "ExportEmailToMHTWithCustomTimezone_out.mhtml", mht_save_options)
```
### **Exportando Correo Electrónico a EML**
El siguiente fragmento de código muestra cómo exportar correo electrónico a eml.

```py
from aspose.email import MailMessage, SaveOptions

# Cargar el archivo EML
msg = MailMessage.load(data_dir + "message.eml")

# Guardar el mensaje de correo electrónico como EML
msg.save(data_dir + "ExporttoEml_out.eml", SaveOptions.default_eml)
```
### **Guardando Mensaje como HTML**
La clase [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) permite exportar el cuerpo del mensaje a HTML con la opción de guardar recursos embebidos. El siguiente fragmento de código muestra cómo guardar el mensaje como HTML donde el valor predeterminado de embed_resources es verdadero.

```py
from aspose.email import MailMessage, SaveOptions, HtmlSaveOptions, HtmlFormatOptions

# Cargar el archivo EML
message = MailMessage.load(data_dir + "message.eml")

# Guardar el mensaje de correo electrónico como HTML
message.save(data_dir + "SaveAsHTML_out.html", SaveOptions.default_html)

# O

eml = MailMessage.load(data_dir + "message.eml")
options = HtmlSaveOptions()
options.embed_resources = False
options.html_format_options = (
    HtmlFormatOptions.WRITE_HEADER
    | HtmlFormatOptions.WRITE_COMPLETE_EMAIL_ADDRESS
)  # guardar los encabezados del mensaje en HTML de salida usando las opciones de formato
eml.save(data_dir + "SaveAsHTML1_out.html", options)
```

### **Guardando Mensaje como Archivo de Plantilla Outlook (.oft)**
El siguiente fragmento de código muestra cómo guardar un mensaje como archivo de plantilla Outlook (.oft).

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "asunto de plantilla", "Cuerpo de la plantilla")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```