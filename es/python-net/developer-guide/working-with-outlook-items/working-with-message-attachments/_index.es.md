---
title: "Trabajar con archivos adjuntos de mensajes"
url: /es/python-net/working-with-message-attachments/
weight: 70
type: docs
---


## **Administración de archivos adjuntos con Aspose Outlook**
Cómo crear y guardar archivos de mensajes de Outlook (MSG) se explicó cómo crear y guardar mensajes y cómo crear archivos MSG con archivos adjuntos. En este artículo se explica cómo administrar los archivos adjuntos de Microsoft Outlook con Aspose.Email. Se accede a los archivos adjuntos de un archivo de mensajes y se guardan en el disco mediante la propiedad Attachments de la clase MapiMessage. La propiedad Attachments es una colección de tipo MAPIAttachmentCollection.

### **Comprueba si el archivo adjunto está en línea o es normal**

Los archivos adjuntos «en línea» y «normales» se refieren a la forma en que se incluyen en un mensaje de correo electrónico. **Regular** los archivos adjuntos son archivos adjuntos de la manera tradicional. Por lo general, se muestran en una lista dentro del cliente de correo electrónico y el destinatario puede descargarlos y guardarlos en un almacenamiento local. **Inline** los archivos adjuntos, también conocidos como imágenes incrustadas o en línea, se utilizan normalmente para incluir imágenes u otros medios en el cuerpo del correo electrónico. No se muestran en una lista separada, sino que se muestran directamente dentro del contenido del correo electrónico, por ejemplo, en el cuerpo del correo electrónico. Esto te permite incluir imágenes u otros medios que formen parte del contenido del mensaje. El ejemplo de código que aparece a continuación muestra cómo determinar si un archivo adjunto está integrado o es normal:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Guardar archivos adjuntos del archivo de mensajes de Outlook (MSG)**

Para guardar los archivos adjuntos de un archivo MSG:

1. Recorra la colección MapiAttachmentCollection y obtenga los archivos adjuntos individuales.
1. Para guardar los archivos adjuntos, llame al método Save () de la clase MapiAttachment.

El siguiente fragmento de código muestra cómo guardar los archivos adjuntos en el disco local.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Create an instance of MapiMessage from file
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Iterate through the attachments collection
for attachment in message.attachments:
    # Save the individual attachment
    attachment.save(data_dir + attachment.file_name)
```

### **Obtener archivos adjuntos de mensajes de correo anidados**

Los archivos adjuntos OLE incrustados también aparecen en la colección Attachment de la clase MapiMessage. En el siguiente ejemplo de código, se analiza un archivo de mensajes en busca de datos adjuntos incrustados y se guarda en el disco. El método estático fromProperties () de la clase MapiMessage puede crear un mensaje nuevo a partir de un archivo adjunto incrustado. El siguiente fragmento de código muestra cómo obtener archivos adjuntos de mensajes de correo anidados.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Create a MapiMessage object from the individual attachment
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Create an object of type MailMessageInterpreter from the above message and save the embedded message to a file on disk
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Eliminar archivos adjuntos**

La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar los archivos adjuntos de los archivos de mensajes de Microsoft Outlook (.msg):

- Llama al método removeAttachments (). Toma la ruta del archivo de mensajes como parámetro. Se implementa como un método estático público, por lo que no es necesario crear una instancia del objeto.

El siguiente fragmento de código muestra cómo eliminar los archivos adjuntos.


```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

También puedes llamar al método estático destoryAttachment () de la clase MapiMessage. Funciona más rápido que removeAttachment (), porque el método removeAttachment () analiza el archivo de mensajes.

```py
import aspose.email as ae

# Destroy attachments in the MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Agregar archivos adjuntos de MSG**

Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en archivos adjuntos, ya sea como mensajes normales o incrustados. La colección MAPIAttachmentCollection proporciona elementos sobrecargados del método Add para crear mensajes de Outlook con ambos tipos de archivos adjuntos.
{{% alert %}}
**¡Pruébalo!**

Agregue o elimine archivos adjuntos de correo electrónico en línea con la versión gratuita [**Aplicación Aspose.Email Editor**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un adjunto de referencia a un MAPIMessage**

El «archivo adjunto de referencia» normalmente se refiere a un archivo adjunto que contiene una referencia o un enlace a un recurso externo, en lugar del archivo propiamente dicho. Estas referencias se suelen utilizar en los correos electrónicos HTML para vincular a imágenes o recursos externos alojados en un servidor remoto. En lugar de incrustar todo el archivo, un adjunto de referencia incluye una URL o una referencia al contenido externo.

Aspose.Email proporciona un conjunto de herramientas para la visualización correcta de los archivos adjuntos de referencia que se presentan en el siguiente ejemplo de código:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Add reference attachment
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# Also, you can set additional attachment properties
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Finally save the message
msg.save("msg_with_ref_attach.msg")
```
### **Insertar un mensaje como archivo adjunto**
El siguiente fragmento de código muestra cómo hacer que los archivos MSG de Outlook incrustados en un archivo MSG contengan un PR_ATTACH_METHOD cuyo valor es igual a 5.

```py
import aspose.email as ae

# Create a new MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "This is a message body")

# Load the attachment message
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Add the attachment to the message
message.attachments.add("Weekly report.msg", attach_msg)

# Save the message with the embedded message attachment
message.save("WithEmbeddedMsg_out.msg")
```
### **Lea los mensajes incrustados de los archivos adjuntos**
El siguiente fragmento de código muestra cómo leer un mensaje incrustado a partir de un archivo adjunto.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.from_file(file_name)

# Check if the first attachment is an Outlook message
if message.attachments[0].object_data.is_outlook_message:
    # Get the embedded message as MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Perform further operations with the embedded message
    # ...
```
## **Inserción y reemplazo de archivos adjuntos**
La API Aspose.Email ofrece la capacidad de insertar archivos adjuntos en un índice específico en el mensaje principal. También ofrece la posibilidad de reemplazar el contenido de un adjunto por otro adjunto de mensaje. El siguiente fragmento de código muestra cómo insertar y reemplazar archivos adjuntos.
### **Insertar en una ubicación específica**
La API Aspose.Email ofrece la capacidad de insertar un archivo adjunto de MSG en un mensaje principal mediante el método de inserción MapiAttachmentCollection Insert de MapiAttachmentCollection Insert (int index, string name, mapiMessage msg). En el siguiente fragmento de código, se muestra cómo insertar en una ubicación específica.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Insert the loaded attachment at index 1
message.attachments.insert(1, "new 11", get_data)
```
### **Reemplazar el contenido del archivo adjunto**
Esto se puede usar para reemplazar el contenido de los archivos adjuntos incrustados por otros nuevos mediante el método Replace. Sin embargo, no se puede usar para insertar datos adjuntos con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con Collection.count = 2. El siguiente fragmento de código muestra cómo reemplazar el contenido de los archivos adjuntos.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Replace the attachment at index 1 with the loaded attachment
message.attachments.replace(1, "new 1", get_data)
```
### **Cambiar el nombre de un archivo adjunto en un MAPIMessage**

Es posible modificar los nombres para mostrar de los archivos adjuntos de los mensajes de correo electrónico cargados desde un archivo. El ejemplo de código que aparece a continuación muestra cómo hacerlo:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "New display name 1"
msg.attachments[1].display_name = "New display name 2"
```