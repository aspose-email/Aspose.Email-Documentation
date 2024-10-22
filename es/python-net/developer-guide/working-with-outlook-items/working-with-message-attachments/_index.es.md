---
title: "Trabajando con Archivos Adjuntos de Mensajes"
url: /es/python-net/working-with-message-attachments/
weight: 70
type: docs
---

## **Gestión de Adjuntos con Aspose Outlook**
Crear y guardar archivos de mensajes de Outlook (MSG) explicó cómo crear y guardar mensajes, y cómo crear archivos MSG con adjuntos. Este artículo explica cómo gestionar los adjuntos de Microsoft Outlook con Aspose.Email. Los adjuntos de un archivo de mensaje se acceden y guardan en el disco usando la propiedad Attachments de la clase MapiMessage. La propiedad Attachments es una colección del tipo MapiAttachmentCollection.

### **Verificar si el Adjunto es En Línea o Regular**

Los adjuntos "En Línea" y "Regulares" se refieren a la forma en que están incluidos en un mensaje de correo electrónico. Los adjuntos **Regulares** son archivos adjuntos de la manera tradicional. Se muestran típicamente en una lista dentro del cliente de correo electrónico y pueden ser descargados por un destinatario y guardados en un almacenamiento local. Los adjuntos **En Línea**, también conocidos como imágenes integradas o en línea, se utilizan típicamente para incluir imágenes u otros medios dentro del cuerpo del correo electrónico. No se muestran en una lista separada, sino que se muestran directamente dentro del contenido del correo electrónico, como en el cuerpo del correo electrónico. Esto te permite incluir imágenes u otros medios que son parte del contenido del mensaje. El siguiente ejemplo de código demuestra cómo determinar si un adjunto es en línea o regular:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Guardar Adjuntos de un Archivo de Mensaje (MSG) de Outlook**

Para guardar adjuntos de un archivo MSG:

1. Itera a través de la colección MapiAttachmentCollection y obtiene los adjuntos individuales.
1. Para guardar los adjuntos, llama al método Save() de la clase MapiAttachment.

El siguiente fragmento de código te muestra cómo guardar adjuntos en el disco local.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Crear una instancia de MapiMessage desde el archivo
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Iterar a través de la colección de adjuntos
for attachment in message.attachments:
    # Guardar el adjunto individual
    attachment.save(data_dir + attachment.file_name)
```

### **Obteniendo Adjuntos de Mensajes de Correo Anidados**

Los adjuntos OLE integrados también aparecen en la colección Attachment de la clase MapiMessage. El siguiente ejemplo de código analiza un archivo de mensaje en busca de adjuntos de mensajes incrustados y los guarda en el disco. El método estático FromProperties() de la clase MapiMessage puede crear un nuevo mensaje a partir de un adjunto integrado. El siguiente fragmento de código te muestra cómo obtener adjuntos de mensajes de correo anidados.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Crear un objeto MapiMessage desde el adjunto individual
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Crear un objeto de tipo MailMessageInterpreter a partir del mensaje anterior y guardar el mensaje incrustado en un archivo en el disco
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Eliminar Adjuntos**

La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar adjuntos de archivos de Mensajes de Microsoft Outlook (.msg):

- Llama al método RemoveAttachments(). Toma la ruta del archivo del mensaje como parámetro. Se implementa como un método estático público, por lo que no necesitas crear una instancia del objeto.

El siguiente fragmento de código te muestra cómo eliminar adjuntos.

```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

También puedes llamar al método estático DestroyAttachment() de la clase MapiMessage. Funciona más rápido que RemoveAttachment(), porque el método RemoveAttachment() analiza el archivo del mensaje.

```py
import aspose.email as ae

# Destruir adjuntos en la MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Agregar Adjuntos MSG**

Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en los adjuntos, ya sea como mensajes regulares o incrustados. La MapiAttachmentCollection proporciona miembros sobrecargados del método Add para crear mensajes de Outlook con ambos tipos de adjuntos.
{{% alert %}}
**¡Pruébalo!**

Agrega o elimina adjuntos de correos electrónicos en línea con la gratuita [**Aplicación Editor de Aspose.Email**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un Adjunto de Referencia a un MapiMessage**

"Adjunto de referencia" se refiere típicamente a un adjunto que contiene una referencia o enlace a un recurso externo en lugar del archivo real en sí. Estas referencias a menudo se utilizan en correos electrónicos HTML para vincular a imágenes o recursos externos alojados en un servidor remoto. En lugar de incrustar el archivo completo, un adjunto de referencia incluye una URL o referencia al contenido externo.

Aspose.Email proporciona un conjunto de herramientas para la correcta visualización de adjuntos de referencia presentadas en el siguiente ejemplo de código:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Agregar adjunto de referencia
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# También puedes establecer propiedades adicionales del adjunto
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Finalmente guarda el mensaje
msg.save("msg_with_ref_attach.msg")
```
### **Incrustar un Mensaje como Adjuntado**
El siguiente fragmento de código te muestra cómo archivos MSG de Outlook incrustados en un archivo MSG contienen un PR_ATTACH_METHOD cuyo valor es 5.

```py
import aspose.email as ae

# Crear un nuevo MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "Este es el cuerpo del mensaje")

# Cargar el mensaje de adjunto
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Agregar el adjunto al mensaje
message.attachments.add("Weekly report.msg", attach_msg)

# Guardar el mensaje con el adjunto del mensaje incrustado
message.save("WithEmbeddedMsg_out.msg")
```
### **Leer Mensajes Incrustados de Adjuntos**
El siguiente fragmento de código te muestra cómo leer un mensaje incrustado de un adjunto.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Cargar el MapiMessage desde el archivo
message = ae.mapi.MapiMessage.from_file(file_name)

# Comprobar si el primer adjunto es un mensaje de Outlook
if message.attachments[0].object_data.is_outlook_message:
    # Obtener el mensaje incrustado como MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Realizar más operaciones con el mensaje incrustado
    # ...
```
## **Inserción y Reemplazo de Adjuntos**
La API de Aspose.Email proporciona la capacidad de insertar adjuntos en un índice específico en el mensaje padre. También proporciona la posibilidad de reemplazar el contenido de un adjunto con otro adjunto de mensaje. El siguiente fragmento de código te muestra cómo insertar y reemplazar adjuntos.
### **Insertar en una Ubicación Específica**
La API de Aspose.Email proporciona la capacidad de insertar un adjunto MSG en un MSG padre usando el método Insert de MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). El siguiente fragmento de código te muestra cómo insertar en una ubicación específica.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Cargar el MapiMessage desde el archivo
message = ae.mapi.MapiMessage.load(file_name)

# Guardar el adjunto en un flujo de memoria
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Cargar el adjunto desde el flujo de memoria
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Insertar el adjunto cargado en el índice 1
message.attachments.insert(1, "new 11", get_data)
```
### **Reemplazar el Contenido de un Adjunto**
Esto se puede usar para reemplazar el contenido de un adjunto incrustado con los nuevos usando el método Replace. Sin embargo, no se puede usar para insertar un adjunto con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con collection.Count = 2. El siguiente fragmento de código te muestra cómo reemplazar el contenido de un adjunto.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Cargar el MapiMessage desde el archivo
message = ae.mapi.MapiMessage.load(file_name)

# Guardar el adjunto en un flujo de memoria
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Cargar el adjunto desde el flujo de memoria
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Reemplazar el adjunto en el índice 1 con el adjunto cargado
message.attachments.replace(1, "new 1", get_data)
```
### **Renombrar un Adjunto en un MapiMessage**

Es posible modificar los nombres de visualización de los adjuntos en los mensajes de correo electrónico cargados desde un archivo. El siguiente ejemplo de código muestra cómo hacerlo:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "Nuevo nombre de visualización 1"
msg.attachments[1].display_name = "Nuevo nombre de visualización 2"
```