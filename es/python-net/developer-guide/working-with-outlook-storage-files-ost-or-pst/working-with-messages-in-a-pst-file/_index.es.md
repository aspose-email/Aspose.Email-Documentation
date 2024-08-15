---
title: "Trabajar con mensajes en un archivo PST"
url: /es/python-net/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---


## **Agregar mensajes a archivos PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir mensajes a las subcarpetas de un archivo PST que hayas creado o cargado. Este artículo agrega dos mensajes del disco a la subcarpeta Bandeja de entrada de un PST. Utilice las clases PersonalStorage y FolderInfo para agregar mensajes a los archivos PST. Para agregar mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la carpeta Inbox.
1. Agregue mensajes del disco a la carpeta Bandeja de entrada llamando al método FolderInfo.add_message (). La clase FolderInfo expone el método add_messages, que permite agregar una gran cantidad de mensajes a la carpeta, lo que reduce las operaciones de E/S en el disco y mejora el rendimiento. Puedes encontrar un ejemplo completo más abajo, en Añadir mensajes masivos.

Los fragmentos de código que aparecen a continuación muestran cómo agregar mensajes a una subcarpeta de PST llamada Bandeja de entrada.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Añadir mensajes masivos**
Agregar mensajes individuales a un PST implica más operaciones de E/S en el disco y, por lo tanto, puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes se pueden agregar al PST de forma masiva para minimizar las operaciones de E/S. El método add_messages permite definir un rango de mensajes que se agregarán al PST para mejorar el rendimiento y se puede utilizar en los siguientes escenarios.
### **Carga de mensajes desde un disco**
El siguiente fragmento de código muestra cómo cargar mensajes desde un disco.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Usage
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **Implementación de MapiMessage Collection**
El siguiente fragmento de código muestra cómo implementar MapiMessageCollection.

```py
import os
from aspose.email.mapi import MapiMessage


class MapiMessageEnumerator:
    def __init__(self, path):
        self.files = os.listdir(path)
        self.position = -1

    def __next__(self):
        self.position += 1
        if self.position < len(self.files):
            return MapiMessage.from_file(os.path.join(self.path, self.files[self.position]))
        else:
            raise StopIteration

    def __iter__(self):
        return self


class MapiMessageCollection:
    def __init__(self, path):
        self.path = path

    def __iter__(self):
        return MapiMessageEnumerator(self.path)


# Usage
msg_folder_name = "\\Files\\msg"

message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Do something with each MapiMessage
    pass
```
### **Agregar mensajes de otro PST**
Para agregar mensajes de otro PST, utilice el método FolderInfo.enumerate_MAPI_MESSAGES (). El siguiente fragmento de código muestra cómo agregar mensajes de otro PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Obtener información de mensajes de un archivo PST de Outlook**
En Leer archivos PST de Outlook y obtener información sobre carpetas y subcarpetas, hablamos sobre cómo cargar un archivo PST de Outlook y examinar sus carpetas para obtener los nombres de las carpetas y el número de mensajes que contienen. En este artículo se explica cómo leer todas las carpetas y subcarpetas del archivo PST y cómo mostrar la información sobre los mensajes (por ejemplo, el asunto, el remitente y los destinatarios). El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información sobre los mensajes de estas carpetas, así como de las carpetas de nivel superior, utilice un método recursivo para leer todas las carpetas. El siguiente fragmento de código muestra cómo leer un archivo PST de Outlook y mostrar el contenido de la carpeta y los mensajes de forma recursiva.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Extracción de mensajes de archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y extraer mensajes. A continuación se muestra un fragmento de código que muestra cómo extraer mensajes de un archivo PST.

```python
from aspose.email.storage.pst import *
from aspose.email.mapi import MapiMessage

pst = PersonalStorage.from_file("Outlook.pst")

folderInfo = pst.root_folder

messageInfoCollection = folderInfo.get_contents()

for messageInfo in messageInfoCollection:
   mapi = pst.extract_message(messageInfo)

   print("Subject: " + mapi.subject)
   print("Sender name: " + mapi.sender_name)
   print("Sender email address: " + mapi.sender_email_address)
   print("To: ", mapi.display_to)
   print("Cc: ", mapi.display_cc)
   print("Bcc: ", mapi.display_bcc)
   print("Delivery time: ", str(mapi.delivery_time))
   print("Body: " + mapi.body)
```
### **Extraer un número n de mensajes de un archivo PST**

Para extraer un número específico de mensajes de un archivo PST, utilice *get_contents (start_index, recuento)* método del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) clase. Se necesitan dos parámetros:

- **start_index** - el número del mensaje inicial, por ejemplo el décimo;
- **count** - número total de mensajes a recuperar.

Recuperar solo el subconjunto de mensajes necesario a la vez puede resultar útil para administrar grandes volúmenes de datos de correo electrónico. El siguiente ejemplo de código muestra la implementación de esta función:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Extracts messages starting from 10th index top and extract total 100 messages
messages = folder.get_contents(10, 100)
```
### **Obtener el recuento total de artículos de un archivo PST**

Para recuperar el número total de elementos (como correos electrónicos, citas, tareas, contactos, etc.) presentes en el almacén de mensajes, utilice el *get_total_items_count()* método del [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) clase. Proporciona una forma cómoda de recopilar rápidamente información sobre el tamaño y el volumen de los datos de la tienda. El siguiente fragmento de código muestra cómo obtener el número total de elementos de un archivo PST:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Eliminar mensajes de archivos PST**
Agregar mensajes a archivos PST mostró cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y también puede ser conveniente eliminar los mensajes de forma masiva. Los elementos de un archivo PST se pueden eliminar mediante el método FolderInfo.delete_child_item (). La API también proporciona el método FolderInfo.DELETE_CHILD_ITEMS () para eliminar elementos de forma masiva del archivo PST.
### **Eliminar mensajes de archivos PST**
En este artículo se muestra cómo usar la clase FolderInfo para acceder a carpetas específicas de un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un archivo PST previamente cargado o creado:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la subcarpeta enviada.
1. Elimine los mensajes de la carpeta Enviados llamando al método FolderInfo.DELETE_CHILD_ITEM () y pasando MessageInfo.entry_ID como parámetro. El siguiente fragmento de código muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Eliminar carpetas de archivos PST**

Puede eliminar una carpeta PST moviéndola a la carpeta Elementos eliminados.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Empty folder")
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
La ventaja de este método es que la carpeta eliminada se puede recuperar fácilmente.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```
También puede eliminar permanentemente una carpeta de la carpeta Elementos eliminados, si es necesario.


```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
The *delete_child_item* el método se puede usar para cualquier carpeta si desea eliminar una subcarpeta de forma inmediata y permanente, sin pasar por la carpeta Elementos eliminados.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Eliminar elementos de PST**

En muchos sistemas de mensajería o clientes de correo electrónico, a cada elemento (como un correo electrónico, una cita o una tarea) se le asigna un identificador único denominado ID de entrada. El *delete_item(entry_id)* método del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class toma este ID de entrada como parámetro y elimina el elemento correspondiente del almacén de mensajes. Usa el siguiente código para eliminar un elemento del almacén de mensajes:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Eliminar artículos de forma masiva del archivo PST**
La API Aspose.Email se puede usar para eliminar elementos de forma masiva de un archivo PST. Esto se logra mediante el método delete_child_items (), que acepta una lista de elementos de ID de entrada que hacen referencia a los elementos que se van a eliminar. El siguiente fragmento de código muestra cómo eliminar elementos de forma masiva del archivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Buscar mensajes y carpetas en un PST por criterio**
Los archivos de almacenamiento personal (PST) pueden contener una gran cantidad de datos y la búsqueda de datos que cumplan un criterio específico en archivos tan grandes debe incluir varios puntos de control en el código para filtrar la información. Con la clase PersonalStorageQueryBuilder, Aspose.Email permite buscar registros específicos en un PST en función de un criterio de búsqueda específico. Se pueden buscar mensajes en un PST en función de parámetros de búsqueda como el remitente, el destinatario, el asunto, la importancia del mensaje, la presencia de archivos adjuntos, el tamaño del mensaje e incluso el identificador del mensaje. El PersonalStorageQueryBuilder también se puede usar para buscar subcarpetas.
### **Búsqueda de mensajes y carpetas en PST**
El siguiente fragmento de código muestra cómo usar la clase PersonalStorageQueryBuilder para buscar contenido en un PST según distintos criterios de búsqueda. Por ejemplo, muestra la búsqueda de un PST en función de:

- Importancia del mensaje.
- Clase de mensajes.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos y
- carpetas con un nombre de subcarpeta específico.

```py
from aspose.email.mapi import MapiMessageFlags
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder, MapiImportance

with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")
    builder = PersonalStorageQueryBuilder()

    # High importance messages
    builder.importance.equals(2)
    messages = folder.get_contents(builder.get_query())
    print("Messages with High Imp:", messages.count)

    builder = PersonalStorageQueryBuilder()
    builder.message_class.equals("IPM.Note")
    messages = folder.get_contents(builder.get_query())
    print("Messages with IPM.Note:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Messages with attachments AND high importance
    builder.importance.equals(2)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Messages with atts:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Messages with size > 15 KB
    builder.message_size.greater(15000)
    messages = folder.get_contents(builder.get_query())
    print("Messages size > 15 KB:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Unread messages
    builder.has_no_flags(MapiMessageFlags.READ)
    messages = folder.get_contents(builder.get_query())
    print("Unread:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Unread messages with attachments
    builder.has_no_flags(MapiMessageFlags.READ)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Unread msgs with atts:", messages.count)

    # Folder with name 'SubInbox'
    builder = PersonalStorageQueryBuilder()
    builder.folder_name.equals("SubInbox")
    folders = folder.get_sub_folders(builder.get_query())
    print("Folder having subfolder:", folders.count)

    builder = PersonalStorageQueryBuilder()
    # Folders with subfolders
    builder.has_subfolders()
    folders = folder.get_sub_folders(builder.get_query())
    print("Folders with subfolders:", folders.count)
```
### **Búsqueda de una cadena en PST con el parámetro Ignorar mayúsculas y minúsculas**
El siguiente fragmento de código muestra cómo buscar una cadena en PST con el parámetro ignore mayúsculas y minúsculas.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Búsqueda de asuntos de mensajes por varias palabras clave en un archivo PST**

Recupere mensajes o elementos específicos de un archivo de almacenamiento personal (PST) o de un almacén de mensajes mediante la implementación del *ya sea (consulta 1, consulta 2)* método del [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) clase en tu proyecto. Se necesitan dos parámetros que te permiten combinar dos consultas diferentes, la consulta 1 y la consulta 2, y encontrar un asunto del mensaje que coincida con cualquiera de las dos palabras especificadas. Consulta el ejemplo de código que aparece a continuación:

```python
import aspose.email as ae

builder1 = ae.storage.pst.PersonalStorageQueryBuilder()
builder1.subject.contains("Review") # 'Review' is key word for the search

builder2 = ae.storage.pst.PersonalStorageQueryBuilder()
builder2.subject.contains("Error") # 'Error' is also key word for the search

builder = ae.storage.pst.PersonalStorageQueryBuilder()
# message subjects must contain 'Review' or 'Error' words
builder.either(builder1.get_query(), builder2.get_query())


pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")
messages = folder.get_contents(builder.get_query())

for message in messages:
    print(f"Message: {message.subject}")
```

## **Mover elementos a otras carpetas del archivo PST**
Aspose.Email permite mover elementos de una carpeta de origen a otra carpeta del mismo archivo de almacenamiento personal (PST). Esto incluye:

- Mover una carpeta especificada a una nueva carpeta principal.
- Mover un mensaje específico a una nueva carpeta.
- Mover el contenido a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta principal.

El siguiente fragmento de código muestra cómo mover elementos como mensajes y carpetas de una carpeta de origen a otra carpeta del mismo archivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Actualización de las propiedades de los mensajes en un archivo PST**
A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y otras similares. La actualización de un mensaje en un archivo PST, con estos cambios en las propiedades del mensaje, se puede realizar mediante el método FolderInfo.change_messages. En este artículo se muestra cómo actualizar los mensajes de forma masiva en un archivo PST para modificar las propiedades. En el siguiente fragmento de código, se muestra cómo actualizar las propiedades de los mensajes de forma masiva para varios mensajes de un archivo PST.

```py
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder
from aspose.email.mapi import MapiPropertyTag, MapiProperty, MapiPropertyCollection

pst_file_path = data_dir + "ya4demia04vb.pst"

# Load the Outlook PST file
with PersonalStorage.from_file(pst_file_path) as personal_storage:
    # Get the required subfolder
    inbox = personal_storage.root_folder.get_sub_folder("Inbox")

    # Find messages having From = "someuser@domain.com"
    query_builder = PersonalStorageQueryBuilder()
    query_builder.from_address.contains("someuser@domain.com")

    # Get contents from query
    messages = inbox.get_contents(query_builder.get_query())

    # Save (MessageInfo, EntryIdString) in a list
    change_list = [message_info.entry_id_string for message_info in messages]

    # Compose the new properties
    updated_properties = MapiPropertyCollection()
    updated_properties.add(
        MapiPropertyTag.SUBJECT_W,
        MapiProperty(MapiPropertyTag.SUBJECT_W, "New Subject".encode("utf-16le"))
    )
    updated_properties.add(
        MapiPropertyTag.IMPORTANCE,
        MapiProperty(MapiPropertyTag.IMPORTANCE, bytearray([0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]))
    )

    # Update messages having From = "someuser@domain.com" with new properties
    inbox.change_messages(change_list, updated_properties)
```
## **Actualización de propiedades personalizadas en un archivo PST**
A veces es necesario marcar los elementos que se procesan en el archivo PST. La API Aspose.Email permite lograr esto utilizando MapiProperty y MapInAmedProperty. Los siguientes métodos son útiles para lograrlo.

- ctor MapInAmedProperty (PropertyTag largo, identificador de nombre de cadena, UUID, PropertyGuid, byteArray [] PropertyValue)
- ctor MapInAmedProperty (PropertyTag largo, identificador de nombre largo, UUID PropertyGuid, byteArray [] PropertyValue)
- FolderInfo.change_messages (MAPIPropertyCollection UpdatedProperties): cambia todos los mensajes de la carpeta
- PersonalStorage.change_messages (string EntryID, MapiPropertyCollection UpdatedProperties): cambia las propiedades de los mensajes

```py
from uuid import UUID
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import MapiNamedProperty, MapiPropertyCollection
from aspose.email.mapi import MapiPropertyType, MapiProperty, MapiPropertyTag

def generate_named_property_tag(index, data_type):
    return (((0x8000 | index) << 16) | data_type) & 0x00000000FFFFFFFF

def run():
    # Load the Outlook file
    pst_file_path = data_dir + "my.pst"

    with PersonalStorage.from_file(pst_file_path) as personal_storage:
        test_folder = personal_storage.root_folder.get_sub_folder("Inbox")

        # Create the collection of message properties for adding or updating
        new_properties = MapiPropertyCollection()

        # Normal, Custom, and PidLidLogFlags named properties
        mapi_property = MapiProperty(
            MapiPropertyTag.ORG_EMAIL_ADDR_W,
            "test_address@org.com".encode("utf-16le")
        )
        named_property1 = MapiNamedProperty(
            generate_named_property_tag(0, MapiPropertyType.LONG),
            "ITEM_ID",
            UUID("00000000-0000-0000-0000-000000000000"),
            bytearray([0x7B, 0x00, 0x00, 0x00])
        )
        named_property2 = MapiNamedProperty(
            generate_named_property_tag(1, MapiPropertyType.LONG),
            0x0000870C,
            UUID("0006200A-0000-0000-C000-000000000046"),
            bytearray([0x00, 0x00, 0x00, 0x00])
        )
        new_properties.add(named_property1.tag, named_property1)
        new_properties.add(named_property2.tag, named_property2)
        new_properties.add(mapi_property.tag, mapi_property)
        test_folder.change_messages(test_folder.enumerate_messages_entry_id(), new_properties)

# Usage
run()
```
## **Extraer archivos adjuntos sin extraer el mensaje completo**
La API Aspose.Email se puede usar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. Para ello, se puede utilizar el método extract_attachments de IewsClient. El siguiente fragmento de código muestra cómo extraer los archivos adjuntos sin extraer el mensaje completo.

```py
from aspose.email.storage.pst import PersonalStorage


with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")

    for message_info in folder.enumerate_messages_entry_id():
        attachments = personal_storage.extract_attachments(message_info)

        if attachments.count != 0:
            for attachment in attachments:
                if attachment.long_file_name is not None and attachment.long_file_name.endswith(".msg"):
                    continue
                else:
                    attachment.save(data_dir + attachment.long_file_name)
```
## **Agregar archivos a PST**
La funcionalidad clave de Microsoft Outlook es administrar correos electrónicos, calendarios, tareas, contactos y entradas del diario. Además, los archivos también se pueden agregar a una carpeta PST y el PST resultante guarda un registro de los documentos agregados. Aspose.Email ofrece la posibilidad de agregar archivos a una carpeta de la misma manera, además de agregar mensajes, contactos, tareas y entradas de diario a PST. El siguiente fragmento de código muestra cómo agregar documentos a una carpeta PST mediante Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}
