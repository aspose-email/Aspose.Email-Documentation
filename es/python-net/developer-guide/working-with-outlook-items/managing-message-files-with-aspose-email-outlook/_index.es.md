---
title: "Gestión de archivos de mensajes con Aspose.Email.Outlook"
url: /es/python-net/gestion-de-archivos-de-mensajes-con-aspose-email-outlook/
weight: 30
type: docs
---

## **Determinar el tipo de elemento MAPI en una carpeta PST**

Un archivo PST contiene típicamente varios tipos de datos, como mensajes de correo electrónico, eventos del calendario, contactos, y más. La clase [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) de Aspose.Email le permite acceder y categorizar diferentes tipos de elementos MAPI dentro de un archivo PST. El siguiente código demuestra cómo determinar el tipo de un elemento MAPI en una carpeta PST:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Obtener el tipo de clase basado en msg.SupportedType
    item_type = msg.supported_type

    # Tipo no soportado. No se puede acceder como tipo de elemento apropiado.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Tipo de elemento no soportado")
    # Un mensaje de correo electrónico.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # Puede acceder a las propiedades de MapiMessage allí.
        # Un asunto por ejemplo
        print(msg.subject)
    # Un elemento de contacto. Se puede acceder como MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiContact allí. 
        # Un name_info.display_name por ejemplo. 
        print(contact.name_info.display_name)
    # Un elemento del calendario. Se puede acceder como MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiCalendar allí. 
        # Una ubicación por ejemplo. 
        print(calendar.location)
    # Una lista de distribución. Se puede acceder como MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiDistributionList allí
    # Una entrada de diario. Se puede acceder como MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiJournal allí
    # Una nota adhesiva. Se puede acceder como MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiNote allí
    # Un elemento de tarea. Se puede acceder como MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # Puede acceder a las propiedades de MapiTask allí

```

## **Convertir MSG a mensaje MIME**
La API de Aspose.Email proporciona la capacidad de convertir un archivo MSG a un mensaje MIME usando el método ToMailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Establecer tiempo de espera para la conversión y carga de un mensaje**

Para limitar el tiempo en milisegundos de la conversión del mensaje (valor predeterminado 3 seg), se utiliza la propiedad **timeout** de la clase [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class).

Aquí se muestra cómo puede establecer un tiempo de espera para los procesos de conversión y carga de mensajes:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

Al establecer un tiempo de espera para los procesos de conversión y carga de mensajes, puede controlar el tiempo máximo que se permite que estas operaciones se ejecuten. Después de establecer el tiempo de espera, puede proceder con sus procesos de conversión y carga de mensajes.

## **Procesamiento de archivos de plantilla de Outlook (OFT)**

### **Cargar, modificar y guardar un archivo OFT**

Las plantillas de Outlook (OFT) ofrecen una forma conveniente de simplificar el proceso de envío de mensajes de correo electrónico repetitivos. En lugar de componer el mismo correo electrónico desde cero cada vez, puede crear un mensaje en Outlook y guardarlo como una plantilla de Outlook (OFT). Más tarde, siempre que necesite enviar un mensaje similar, puede generarlo rápidamente a partir de la plantilla. Este enfoque le ahorra el esfuerzo de reescribir el mismo contenido en el cuerpo del mensaje, especificar la línea de asunto, el formato y más.

La clase [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) de Aspose.Email proporciona una herramienta poderosa para cargar y manipular archivos de plantilla de Outlook (OFT). Una vez que una plantilla de Outlook se carga en una instancia de la clase MailMessage, puede actualizar fácilmente propiedades como el remitente, destinatario, cuerpo del mensaje, asunto y varios otros atributos.

```py
import aspose.email as ae

# Cargar el archivo OFT
oft_file_path = "your_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Actualizar propiedades según sea necesario
mail_message.subject = "Asunto actualizado"
mail_message.body = "Texto del cuerpo actualizado."

# Guardar el mensaje actualizado como un archivo MSG
msg_file_path = "updated_message.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Mensaje actualizado guardado en {msg_file_path}")
```
Después de realizar las actualizaciones necesarias, puede enviar el correo electrónico usando la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class):

```py
# Enviar el correo electrónico
smtpClient.send(message)
```

### **Guardar archivo MSG de Outlook como plantilla**

Para este propósito, puede usar la clase [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) para crear un correo electrónico, luego guardarlo como un archivo OFT. El siguiente ejemplo de código le mostrará cómo guardar un correo electrónico como una plantilla de Outlook:

```py
import aspose.email as ae

# Crear un nuevo MailMessage
message = ae.MailMessage()
message.subject = "Plantilla de Outlook de ejemplo"
message.html_body = "<html><body>Este es el cuerpo del correo electrónico.</body></html>"
message.from_address = ae.MailAddress("your.email@example.com", "Su Nombre")

# Guardar el MailMessage como un archivo de plantilla de Outlook (OFT)
oft_file_path = "sample_template.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Plantilla de Outlook guardada como {oft_file_path}")
```
### **OFT o MSG: Determinar el tipo de un MapiMessage**

El siguiente fragmento de código ilustra cómo determinar si un mensaje MAPI cargado representa un mensaje de correo electrónico estándar o una plantilla de Outlook (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # devuelve falso

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # devuelve verdadero
```
Después de cargar el archivo MSG, el código verifica si la propiedad **is_template** de la clase [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) es True o False. En caso de que devuelva *falso*, el mensaje cargado es un mensaje de correo electrónico estándar, no una plantilla de Outlook; de lo contrario, si devuelve *verdadero*, el mensaje no es un mensaje de correo electrónico estándar, es una plantilla de Outlook.

### **Guardar MapiMessage o MailMessage como OFT**

La clase [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) es una clase base abstracta para clases que permiten al usuario especificar opciones adicionales al guardar un MailMessage en un formato particular. El siguiente ejemplo de código demuestra cómo guardar un mensaje en formato OFT:

```py
import aspose.email as ae

# Guardar el MailMessage en formato OFT
eml = ae.MailMessage.load("message.eml")

eml.save("message.oft", ae.SaveOptions.default_oft)

# o forma alternativa 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# o forma alternativa 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# Guardar el MapiMessage en formato OFT
msg = ae.mapi.MapiMessage.load("message.msg")

msg.save("message.oft", ae.SaveOptions.default_oft)

# o forma alternativa 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)

# o forma alternativa 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)
```

## **Gestionar mensajes con firmas digitales**

La biblioteca proporciona la clase [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class), una clase base abstracta para clases que permiten al usuario especificar opciones adicionales al cargar un MailMessage desde un formato particular. La opción de conservación de firma está configurada por defecto.

### **Convertir de EML a MSG conservando la firma**

El siguiente ejemplo de código muestra cómo cargar un mensaje, convertirlo a formato MSG y guardarlo como MSG (la firma se conserva por defecto):

```python

import aspose.email as ae

# Cargar el mensaje de correo
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Guardar como MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

### **Convertir mensajes S/MIME de MSG a EML**

Aspose.Email le permite convertir de MSG a EML conservando una firma digital, como se muestra en el siguiente fragmento de código.

```python
import aspose.email as ae

# Cargar el mensaje de correo
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Guardar archivo en disco
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
## **Establecer categoría de color para archivos MSG de Outlook**

A veces puede necesitar diferenciar correos electrónicos de particular importancia y organizarlos visualmente. La biblioteca proporciona una manera de hacerlo asignando un color específico a un elemento de mensaje. Cuando establece una categoría de color para un elemento, le permite identificar y localizar fácilmente elementos relacionados de un vistazo. Use la clase [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) para establecer la categoría de color para un mensaje como en el siguiente ejemplo de código:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Agregar dos categorías
ae.mapi.FollowUpManager.add_category(msg, "Categoría Púrpura")
ae.mapi.FollowUpManager.add_category(msg, "Categoría Roja")

# Recuperar la lista de categorías disponibles
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Eliminar la categoría especificada y luego limpiar todas las categorías
ae.mapi.FollowUpManager.remove_category(msg, "Categoría Roja")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Acceso a la información de seguimiento desde el archivo MSG**

### **Extraer información de recibo de lectura y entrega**

El siguiente ejemplo de código muestra cómo extraer información de destinatarios y su estado de seguimiento desde un mensaje de Outlook (archivo MSG):

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Destinatario: {recipient.display_name}")
    print(f"Hora de entrega:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Hora de lectura:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Creando mensajes de reenvío y respuesta**

Aspose.Email proporciona formas directas de crear mensajes de reenvío y respuesta basados en los existentes.

### **Creando un mensaje de reenvío**

Puede usar la clase [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) para crear un mensaje de reenvío configurando el mensaje fuente, remitente, destinatarios, asunto y cuerpo. Los mensajes de reenvío pueden incluir el mensaje original como un archivo adjunto o como el cuerpo del mensaje reenviado. Tiene la flexibilidad de personalizar propiedades adicionales como archivos adjuntos, encabezados y opciones de formato. El siguiente ejemplo de código muestra cómo crear un mensaje de reenvío:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")

```

### **Creando un mensaje de respuesta**

La clase [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) se utiliza para configurar las opciones de respuesta, incluidos el mensaje fuente, remitente, destinatarios, modo de respuesta, prefijo de asunto y el cuerpo del mensaje de respuesta. Los mensajes de respuesta pueden crearse en diferentes modos de respuesta como "Responder al Remitente" o "Responder a Todos" según su requerimiento. Puede personalizar diversas propiedades como archivos adjuntos, encabezados y opciones de formato para el mensaje de respuesta. El siguiente ejemplo de código muestra cómo crear un mensaje de respuesta:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Establecer propiedades de ReplyMessageBuilder
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Estimado amigo,</b></p> Lo que quiero hacer es presentar a mi coautor y co-profesor. <p><a href=\"www.google.com\">Este es un primer enlace</a></p><p><a href=\"www.google.com\">Este es un segundo enlace</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")

```