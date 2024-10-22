---
title: "Trabajando con Mensajes en un Archivo PST"
url: /es/python-net/working-with-messages-in-a-pst-file/
weight: 100
type: docs
---

## **Agregar Mensajes a Archivos PST**
Crear un Nuevo Archivo PST y Agregar Subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar mensajes a las subcarpetas de un archivo PST que has creado o cargado. Este artículo agrega dos mensajes desde el disco a la subcarpeta Bandeja de entrada de un PST. Usa las clases PersonalStorage y FolderInfo para agregar mensajes a archivos PST. Para agregar mensajes a la carpeta Bandeja de entrada de un archivo PST:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la carpeta Bandeja de entrada.
1. Agrega mensajes desde el disco a la carpeta Bandeja de entrada llamando al método FolderInfo.add_message(). La clase FolderInfo expone el método add_messages que permite agregar un gran número de mensajes a la carpeta, reduciendo las operaciones I/O en disco y mejorando el rendimiento. Un ejemplo completo se puede encontrar más abajo, en Agregar Mensajes en Masa.

Los fragmentos de código a continuación muestran cómo agregar mensajes a una subcarpeta PST llamada Bandeja de entrada.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Agregar Mensajes en Masa**
Agregar mensajes individuales a un PST implica más operaciones I/O en disco y, por lo tanto, puede ralentizar el rendimiento. Para mejorar el rendimiento, los mensajes se pueden agregar al PST en modo masivo para minimizar las operaciones I/O. El método add_messages te permite definir un rango de mensajes que se agregarán al PST para mejorar el rendimiento y se puede usar en los siguientes escenarios.
### **Cargar Mensajes desde Disco**
El siguiente fragmento de código te muestra cómo cargar mensajes desde disco.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Uso
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **Implementación de MapiMessageCollection**
El siguiente fragmento de código te muestra cómo implementar MapiMessageCollection.

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


# Uso
msg_folder_name = "\\Files\\msg"

message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Haz algo con cada MapiMessage
    pass
```
### **Agregar Mensajes desde Otro PST**
Para agregar mensajes desde otro PST, usa el método FolderInfo.enumerate_mapi_messages(). El siguiente fragmento de código te muestra cómo agregar mensajes desde otro PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Obtener Información de Mensajes de un Archivo PST de Outlook**
En Leer Archivo PST de Outlook y Obtener Información de Carpetas y Subcarpetas, discutimos cómo cargar un archivo PST de Outlook y examinar sus carpetas para obtener los nombres de las carpetas y el número de mensajes en ellas. Este artículo explica cómo leer todas las carpetas y subcarpetas en el archivo PST y mostrar la información sobre los mensajes, por ejemplo, asunto, remitente y destinatarios. El archivo PST de Outlook puede contener carpetas anidadas. Para obtener información de mensajes de estas, así como de las carpetas de nivel superior, usa un método recursivo para leer todas las carpetas. El siguiente fragmento de código te muestra cómo leer un archivo PST de Outlook y mostrar el contenido de las carpetas y mensajes de forma recursiva.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Extracción de Mensajes de Archivos PST**

Este artículo muestra cómo leer archivos PST de Microsoft Outlook y extraer mensajes. A continuación se muestra un fragmento de código que muestra cómo extraer mensajes de un archivo PST.

```python
from aspose.email.storage.pst import *
from aspose.email.mapi import MapiMessage

pst = PersonalStorage.from_file("Outlook.pst")

folderInfo = pst.root_folder

messageInfoCollection = folderInfo.get_contents()

for messageInfo in messageInfoCollection:
   mapi = pst.extract_message(messageInfo)

   print("Asunto: " + mapi.subject)
   print("Nombre del remitente: " + mapi.sender_name)
   print("Dirección de correo del remitente: " + mapi.sender_email_address)
   print("Para: ", mapi.display_to)
   print("Cc: ", mapi.display_cc)
   print("Bcc: ", mapi.display_bcc)
   print("Hora de entrega: ", str(mapi.delivery_time))
   print("Cuerpo: " + mapi.body)
```
### **Extracción de n Número de Mensajes de un Archivo PST**

Para extraer un número específico de mensajes de un archivo PST, usa el método *get_contents(start_index, count)* de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Toma dos parámetros:

- **start_index** - el número del mensaje inicial, por ejemplo, el décimo;
- **count** - número total de mensajes a recuperar.

Recuperar solo el subconjunto necesario de mensajes en un momento dado puede ser útil para manejar grandes volúmenes de datos de correo electrónico. El siguiente fragmento de código demuestra la implementación de esta función:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Extrae mensajes comenzando desde el décimo índice y extrae un total de 100 mensajes
messages = folder.get_contents(10, 100)
```
### **Obtener el Total de Elementos de un Archivo PST**

Para recuperar el número total de elementos (como correos electrónicos, citas, tareas, contactos, etc.) presentes en el almacén de mensajes, usa el método *get_total_items_count()* de la clase [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Proporciona una forma conveniente de reunir rápidamente información sobre el tamaño y el volumen de datos dentro del almacén. El siguiente fragmento de código muestra cómo obtener el número total de elementos de un archivo PST:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Eliminar Mensajes de Archivos PST**
Agregar Mensajes a Archivos PST mostró cómo agregar mensajes a archivos PST. Por supuesto, también es posible eliminar elementos (contenidos) de un archivo PST y también puede ser deseable eliminar mensajes en masa. Los elementos de un archivo PST se pueden eliminar utilizando el método FolderInfo.delete_child_item(). La API también proporciona el método FolderInfo.delete_child_items() para eliminar elementos en masa del archivo PST.
### **Eliminación de Mensajes de Archivos PST**
Este artículo muestra cómo usar la clase FolderInfo para acceder a carpetas específicas en un archivo PST. Para eliminar mensajes de la subcarpeta Enviados de un archivo PST que se ha cargado o creado anteriormente:

1. Crea una instancia de la clase FolderInfo y cárgala con el contenido de la subcarpeta Enviados.
1. Elimina mensajes de la carpeta Enviados llamando al método FolderInfo.delete_child_item() y pasando el MessageInfo.entry_id como parámetro. El siguiente fragmento de código te muestra cómo eliminar mensajes de la subcarpeta Enviados de un archivo PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Eliminación de Carpetas de Archivos PST**

Puedes eliminar una carpeta PST moviéndola a la carpeta Elementos eliminados.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Empty folder")
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
La ventaja de este método es que la carpeta eliminada puede ser fácilmente recuperada.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```
También puedes eliminar permanentemente una carpeta de la carpeta Elementos eliminados, si es necesario.


```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
El método *delete_child_item* puede ser utilizado para cualquier carpeta si deseas eliminar inmediatamente y permanentemente una subcarpeta, omitiendo la carpeta Elementos eliminados.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Eliminar Elementos de PST**

En muchos sistemas de mensajería o clientes de correo electrónico, a cada elemento (como un correo electrónico, cita, o tarea) se le asigna un identificador único llamado entry ID. El método *delete_item(entry_id)* de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) toma este entry ID como parámetro y elimina el elemento correspondiente del almacén de mensajes. Usa el siguiente código para eliminar un elemento del almacén de mensajes:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Eliminar Elementos en Masa de un Archivo PST**
La API Aspose.Email se puede usar para eliminar elementos en masa de un archivo PST. Esto se logra utilizando el método delete_child_items() que acepta una lista de elementos Entry ID que se refieren a los elementos a eliminar. El siguiente fragmento de código te muestra cómo eliminar Elementos en masa de un archivo PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Buscar Mensajes y Carpetas en un PST por Criterio**
Los archivos de Almacenamiento Personal (PST) pueden contener una gran cantidad de datos y buscar datos que cumplan con un criterio específico en archivos tan grandes necesita incluir múltiples puntos de control en el código para filtrar la información. Con la clase PersonalStorageQueryBuilder, Aspose.Email hace posible buscar registros específicos en un PST basándose en un criterio de búsqueda especificado. Se puede buscar un PST por mensajes según parámetros de búsqueda como remitente, receptor, asunto, importancia del mensaje, presencia de archivos adjuntos, tamaño del mensaje, e incluso ID del mensaje. El PersonalStorageQueryBuilder también se puede usar para buscar subcarpetas.
### **Buscar Mensajes y Carpetas en PST**
El siguiente fragmento de código te muestra cómo usar la clase PersonalStorageQueryBuilder para buscar contenidos en un PST basado en diferentes criterios de búsqueda. Por ejemplo, muestra cómo buscar un PST según:

- Importancia del mensaje.
- Clase del mensaje.
- Presencia de archivos adjuntos.
- Tamaño del mensaje.
- Mensajes no leídos.
- Mensajes no leídos con archivos adjuntos, y
- carpetas con un nombre de subcarpeta específico.

```py
from aspose.email.mapi import MapiMessageFlags
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder, MapiImportance

with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")
    builder = PersonalStorageQueryBuilder()

    # Mensajes de alta importancia
    builder.importance.equals(2)
    messages = folder.get_contents(builder.get_query())
    print("Mensajes con Alta Importancia:", messages.count)

    builder = PersonalStorageQueryBuilder()
    builder.message_class.equals("IPM.Note")
    messages = folder.get_contents(builder.get_query())
    print("Mensajes con IPM.Note:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensajes con archivos adjuntos Y alta importancia
    builder.importance.equals(2)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Mensajes con adjuntos:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensajes con tamaño > 15 KB
    builder.message_size.greater(15000)
    messages = folder.get_contents(builder.get_query())
    print("Mensajes tamaño > 15 KB:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensajes no leídos
    builder.has_no_flags(MapiMessageFlags.READ)
    messages = folder.get_contents(builder.get_query())
    print("No leídos:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensajes no leídos con archivos adjuntos
    builder.has_no_flags(MapiMessageFlags.READ)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Mensajes no leídos con adjuntos:", messages.count)

    # Carpeta con nombre 'SubInbox'
    builder = PersonalStorageQueryBuilder()
    builder.folder_name.equals("SubInbox")
    folders = folder.get_sub_folders(builder.get_query())
    print("Carpeta que tiene subcarpeta:", folders.count)

    builder = PersonalStorageQueryBuilder()
    # Carpetas con subcarpetas
    builder.has_subfolders()
    folders = folder.get_sub_folders(builder.get_query())
    print("Carpetas con subcarpetas:", folders.count)
```
### **Buscar una Cadena en PST con el Parámetro Ignorar Mayúsculas**
El siguiente fragmento de código te muestra cómo buscar una cadena en PST con el parámetro de ignorar mayúsculas.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Buscar Asuntos de Mensajes por Múltiples Palabras Clave en un Archivo PST**

Recupera mensajes o elementos específicos de un archivo de almacenamiento personal (PST) o almacén de mensajes implementando el método *either(query1, query2)* de la clase [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) en tu proyecto. Toma dos parámetros que te permiten combinar dos consultas diferentes, query1 y query2, y encontrar un asunto de mensaje que coincida con cualquiera de las dos palabras especificadas. Consulta el siguiente ejemplo de código:

```python
import aspose.email as ae

builder1 = ae.storage.pst.PersonalStorageQueryBuilder()
builder1.subject.contains("Revisar") # 'Revisar' es una palabra clave para la búsqueda

builder2 = ae.storage.pst.PersonalStorageQueryBuilder()
builder2.subject.contains("Error") # 'Error' también es una palabra clave para la búsqueda

builder = ae.storage.pst.PersonalStorageQueryBuilder()
# Los asuntos de los mensajes deben contener las palabras 'Revisar' o 'Error'
builder.either(builder1.get_query(), builder2.get_query())


pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")
messages = folder.get_contents(builder.get_query())

for message in messages:
    print(f"Mensaje: {message.subject}")
```

## **Mover Elementos a Otras Carpetas del Archivo PST**
Aspose.Email hace posible mover elementos de una carpeta de origen a otra carpeta en el mismo archivo de Almacenamiento Personal (PST). Esto incluye:

- Mover una carpeta específica a una nueva carpeta principal.
- Mover mensajes específicos a una nueva carpeta.
- Mover el contenido a una nueva carpeta.
- Mover subcarpetas a una nueva carpeta principal.

El siguiente fragmento de código te muestra cómo mover elementos, como mensajes y carpetas, de una carpeta de origen a otra carpeta en el mismo archivo PST.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Actualizar Propiedades de Mensajes en un Archivo PST**
A veces es necesario actualizar ciertas propiedades de los mensajes, como cambiar el asunto, marcar la importancia del mensaje y similares. Actualizar un mensaje en un archivo PST, con tales cambios en las propiedades del mensaje, se puede lograr utilizando el método FolderInfo.change_messages. Este artículo muestra cómo actualizar mensajes en masa en un archivo PST para cambios en las propiedades. El siguiente fragmento de código te muestra cómo actualizar propiedades de mensajes en modo masivo para múltiples mensajes en un archivo PST.

```py
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder
from aspose.email.mapi import MapiPropertyTag, MapiProperty, MapiPropertyCollection

pst_file_path = data_dir + "ya4demia04vb.pst"

# Cargar el archivo PST de Outlook
with PersonalStorage.from_file(pst_file_path) as personal_storage:
    # Obtener la subcarpeta requerida
    inbox = personal_storage.root_folder.get_sub_folder("Inbox")

    # Encontrar mensajes que tengan De = "someuser@domain.com"
    query_builder = PersonalStorageQueryBuilder()
    query_builder.from_address.contains("someuser@domain.com")

    # Obtener contenidos de la consulta
    messages = inbox.get_contents(query_builder.get_query())

    # Guardar (MessageInfo, EntryIdString) en una lista
    change_list = [message_info.entry_id_string for message_info in messages]

    # Componer las nuevas propiedades
    updated_properties = MapiPropertyCollection()
    updated_properties.add(
        MapiPropertyTag.SUBJECT_W,
        MapiProperty(MapiPropertyTag.SUBJECT_W, "Nuevo Asunto".encode("utf-16le"))
    )
    updated_properties.add(
        MapiPropertyTag.IMPORTANCE,
        MapiProperty(MapiPropertyTag.IMPORTANCE, bytearray([0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]))
    )

    # Actualizar mensajes que tengan De = "someuser@domain.com" con nuevas propiedades
    inbox.change_messages(change_list, updated_properties)
```
## **Actualizar Propiedades Personalizadas en un Archivo PST**
A veces es necesario marcar elementos que han sido procesados dentro del archivo PST. La API Aspose.Email permite lograr esto utilizando MapiProperty y MapiNamedProperty. Los siguientes métodos son útiles para lograr esto.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- FolderInfo.change_messages(MapiPropertyCollection updatedProperties) - cambia todos los mensajes en la carpeta
- PersonalStorage.change_messages(string entryId, MapiPropertyCollection updatedProperties) - cambia las propiedades del mensaje

```py
from uuid import UUID
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import MapiNamedProperty, MapiPropertyCollection
from aspose.email.mapi import MapiPropertyType, MapiProperty, MapiPropertyTag

def generate_named_property_tag(index, data_type):
    return (((0x8000 | index) << 16) | data_type) & 0x00000000FFFFFFFF

def run():
    # Cargar el archivo de Outlook
    pst_file_path = data_dir + "my.pst"

    with PersonalStorage.from_file(pst_file_path) as personal_storage:
        test_folder = personal_storage.root_folder.get_sub_folder("Inbox")

        # Crear la colección de propiedades de mensaje para agregar o actualizar
        new_properties = MapiPropertyCollection()

        # Normal, Propiedades personalizadas y PidLidLogFlags
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

# Uso
run()
```
## **Extraer Archivos Adjuntos Sin Extraer el Mensaje Completo**
La API Aspose.Email se puede usar para extraer archivos adjuntos de mensajes PST sin extraer primero el mensaje completo. El método extract_attachments de IEWSClient puede ser utilizado para esto. El siguiente fragmento de código te muestra cómo extraer archivos adjuntos sin extraer el mensaje completo.

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
## **Agregar Archivos a PST**
La funcionalidad clave de Microsoft Outlook es la gestión de correos electrónicos, calendarios, tareas, contactos y entradas de diario. Además, los archivos también se pueden agregar a una carpeta PST y el PST resultante mantiene un registro de los documentos agregados. Aspose.Email proporciona la facilidad de agregar archivos a una carpeta de la misma manera, además de agregar mensajes, contactos, tareas y entradas de diario al PST. El siguiente fragmento de código te muestra cómo agregar documentos a una carpeta PST usando Aspose.Email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}