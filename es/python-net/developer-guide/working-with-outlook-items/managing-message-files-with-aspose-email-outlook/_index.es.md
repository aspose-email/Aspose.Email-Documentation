---
title: "Administración de archivos de mensajes con Aspose.Email.Outlook"
url: /es/python-net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Determinar el tipo de elemento MAPI en una carpeta PST**

Un archivo PST normalmente contiene varios tipos de datos, como mensajes de correo electrónico, eventos del calendario, contactos y más. El [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) la clase Aspose.Email le permite acceder y clasificar diferentes tipos de elementos MAPI dentro de un archivo PST. El código siguiente muestra cómo determinar el tipo de un elemento MAPI en una carpeta PST:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Get the class type based on msg.SupportedType
    item_type = msg.supported_type

    # Non-supported type. It cannot be accessed as appropriate item type.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Item type not supported")
    # An email message.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # You can access to MapiMessage properties there.
        # A subject for example
        print(msg.subject)
    # A contact item. Can be accessed as MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # You can access to MapiContact properties there.
        # A name_info.display_name for example.
        print(contact.name_info.display_name)
    # A calendar item. Can be accessed as MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # You can access to MapiCalendar properties there.
        # A location for example.
        print(calendar.location)
    # A distribution list. Can be accessed as MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # You can access to MapiDistributionList properties there
    # A Journal entry. Can be accessed as MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # You can access to MapiJournal properties there
    # A StickyNote. Can be accessed as MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # You can access to MapiNote properties there
    # A Task item. Can be accessed as MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # You can access to MapiTask properties there

```

## **Conversión de MSG a mensaje MIME**
La API Aspose.Email ofrece la capacidad de convertir un archivo MSG en un mensaje MIME mediante el método ToMailMessage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Configurar el tiempo de espera para la conversión y la carga de un mensaje**

Para limitar el tiempo en milisegundos de la conversión del mensaje (valor predeterminado de 3 segundos), el **timeout** propiedad del [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class) se utiliza la clase.

Así es como puedes establecer un tiempo de espera para los procesos de conversión y carga de mensajes:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

Al establecer un tiempo de espera para los procesos de conversión y carga de mensajes, puede controlar el tiempo máximo que se permite que se ejecuten estas operaciones. Tras configurar el tiempo de espera, puedes continuar con los procesos de conversión y carga de mensajes.


## **Procesamiento de archivos de plantilla de Outlook (OFT)**

### **Cargar, modificar y guardar un archivo OFT**

Las plantillas de Outlook (OFT) ofrecen una forma cómoda de agilizar el proceso de envío de mensajes de correo electrónico repetitivos. En lugar de redactar el mismo correo electrónico desde cero cada vez, puedes crear un mensaje en Outlook y guardarlo como plantilla de Outlook (OFT). Más adelante, siempre que necesite enviar un mensaje similar, podrá generarlo rápidamente a partir de la plantilla. Este enfoque le ahorra el esfuerzo de volver a escribir el mismo contenido en el cuerpo del mensaje, especificando la línea de asunto, el formato, etc.

Aspose.Email's [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) La clase proporciona una poderosa herramienta para cargar y manipular archivos de plantilla de Outlook (OFT). Una vez cargada una plantilla de Outlook en una instancia de la clase MailMessage, puede actualizar fácilmente propiedades como el remitente, el destinatario, el cuerpo del mensaje, el asunto y otros atributos.

```py
import aspose.email as ae

# Load the OFT file
oft_file_path = "your_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Update properties as needed
mail_message.subject = "Updated Subject"
mail_message.body = "Updated body text."

# Save the updated message as an MSG file
msg_file_path = "updated_message.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Updated message saved to {msg_file_path}")
```
Tras realizar las actualizaciones necesarias, puede enviar el correo electrónico a través del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

```py
# Send the email
smtpClient.send(message)
```

### **Guardar el archivo MSG de Outlook como plantilla**

Para ello, puede utilizar el [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) clase para crear un correo electrónico y, a continuación, guardarlo como un archivo OFT. El siguiente ejemplo de código le mostrará cómo guardar un correo electrónico como una plantilla de Outlook:

```py
import aspose.email as ae

# Create a new MailMessage
message = ae.MailMessage()
message.subject = "Sample Outlook Template"
message.html_body = "<html><body>This is the body of the email.</body></html>"
message.from_address = ae.MailAddress("your.email@example.com", "Your Name")

# Save the MailMessage as an Outlook Template (OFT) file
oft_file_path = "sample_template.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Outlook Template saved as {oft_file_path}")
```
### **OFT o MSG: Determine el tipo de un MAPIMessage**

El siguiente fragmento de código muestra cómo determinar si un mensaje MAPI cargado representa un mensaje de correo electrónico estándar o una plantilla de Outlook (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # returns false

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # returns true
```
Tras cargar el archivo MSG, el código comprueba si el **is_template** propiedad del [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) la clase es verdadera o falsa. En caso de que regrese *false*, el mensaje cargado es un mensaje de correo electrónico estándar, no una plantilla de Outlook; de lo contrario, si regresa *true*, el mensaje no es un mensaje de correo electrónico estándar, es una plantilla de Outlook.

### **Guardar MapiMessage o MailMessage como OFT**

The [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) es una clase base abstracta para clases que permite al usuario especificar opciones adicionales al guardar un MailMessage en un formato determinado. El siguiente ejemplo de código muestra cómo guardar un mensaje en formato OFT:

```py
import aspose.email as ae

# Save the MailMessage to OFT format
eml = ae.MailMessage.load("message.eml")

eml.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# Save the MapiMessage to OFT format
msg = ae.mapi.MapiMessage.load("message.msg")

msg.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)
```

## **Administración de mensajes con firmas digitales**

La biblioteca ofrece [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class) class, una clase base abstracta para clases que permiten al usuario especificar opciones adicionales al cargar un MailMessage desde un formato determinado. La opción de conservación de firmas está configurada de forma predeterminada.

### **Convertir de EML a MSG conservando la firma**

El ejemplo de código siguiente muestra cómo cargar un mensaje, convertirlo al formato MSG y guardarlo como MSG (la firma se conserva de forma predeterminada):

```python

import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Save as MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

### **Convierte mensajes S/MIME de MSG a EML**

Aspose.Email le permite convertir de MSG a EML conservando una firma digital, como se muestra en el siguiente fragmento de código.

```python
import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Save File to disk
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
## **Establecer la categoría de color para los archivos MSG de Outlook**

En ocasiones, es posible que necesite diferenciar los correos electrónicos de particular importancia y organizarlos visualmente. La biblioteca proporciona una forma de hacerlo mediante la asignación de un color específico a un elemento del mensaje. Al establecer una categoría de color para un elemento, permite identificar y localizar fácilmente los elementos relacionados de un vistazo. Usa [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) clase para establecer la categoría de color de un mensaje como en el siguiente ejemplo de código:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Add Two categories
ae.mapi.FollowUpManager.add_category(msg, "Purple Category")
ae.mapi.FollowUpManager.add_category(msg, "Red Category")

# Retrieve the list of available categories
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Remove the specified category and then Clear all categories
ae.mapi.FollowUpManager.remove_category(msg, "Red Category")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Acceso a la información de seguimiento desde el archivo MSG**

### **Extraer la información de lectura y recibo de entrega**

El ejemplo de código que aparece a continuación muestra cómo extraer la información del destinatario y su estado de seguimiento de un archivo de mensajes de Outlook (MSG):

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Recipient: {recipient.display_name}")
    print(f"Delivery time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Read time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Creación de mensajes de reenvío y respuesta**

Aspose.Email proporciona formas sencillas de crear, reenviar y responder mensajes basados en los mensajes existentes.

### **Creación de un mensaje de reenvío**

Puedes usar el [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) clase para crear un mensaje de reenvío configurando el mensaje de origen, el remitente, los destinatarios, el asunto y el cuerpo. Los mensajes reenviados pueden incluir el mensaje original como archivo adjunto o como cuerpo del mensaje reenviado. Tiene la flexibilidad de personalizar propiedades adicionales, como los archivos adjuntos, los encabezados y las opciones de formato. El ejemplo de código que aparece a continuación muestra cómo crear un mensaje para reenviar:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")

```

### **Creación de un mensaje de respuesta**

The [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) La clase se usa para configurar los ajustes de respuesta, incluidos el mensaje de origen, el remitente, los destinatarios, el modo de respuesta, el prefijo del asunto y el cuerpo del mensaje de respuesta. Los mensajes de respuesta se pueden crear en diferentes modos de respuesta, como «Responder al remitente» o «Responder a todos», según sus necesidades. Puedes personalizar varias propiedades, como los archivos adjuntos, los encabezados y las opciones de formato del mensaje de respuesta. El ejemplo de código que aparece a continuación muestra cómo crear un mensaje para reenviar:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Set ReplyMessageBuilder Properties
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")

```
