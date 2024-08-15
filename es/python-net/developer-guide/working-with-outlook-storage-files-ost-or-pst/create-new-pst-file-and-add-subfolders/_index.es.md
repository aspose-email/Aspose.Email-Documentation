---
title: "Crear un nuevo archivo PST y agregar subcarpetas"
url: /es/python-net/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---


Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo muestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. Crear un nuevo archivo PST.
1. Cambiar la clase de contenedor de una carpeta.

Use la clase PersonalStorage para crear un archivo PST en alguna ubicación de un disco local. Para crear un archivo PST desde cero:

1. Cree un PST con el método PersonalStorage.create ().
1. Agregue una subcarpeta en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método AddSubFolder.

El siguiente fragmento de código muestra cómo crear un archivo PST y agregar una subcarpeta denominada Bandeja de entrada.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}

## **Comprobación de la coincidencia de clases de contenedor al agregar una carpeta a PST**

Aspose.Email para Python ofrece una solución que mejora el proceso de validación durante la creación de carpetas en archivos PST. Con la propiedad 'enforceContainerClassMatching' de [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) clase, puede garantizar una coincidencia estricta de las clases de contenedores al agregar una nueva carpeta al almacenamiento PST. Esta función ayuda a mantener la jerarquía organizativa dentro del archivo PST al evitar que las clases de contenedores no coincidan. Al establecer «enforceContainerClassMatching» en «true», se generará una excepción si las clases de contenedor de las carpetas principal y secundaria no coinciden, lo que constituye una protección contra estructuras de carpetas incorrectas. El comportamiento predeterminado de esta propiedad es «falso», lo que permite crear carpetas con flexibilidad y, al mismo tiempo, exigir una coincidencia estricta entre las clases de contenedor cuando sea necesario.

En el siguiente ejemplo de código, se muestra el uso de la propiedad 'enforceContainerClassMatching' para controlar si se debe lanzar una excepción al agregar carpetas con clases de contenedor que no coinciden:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
   
    # An exception will not arise. EnforceContainerClassMatching is False by default.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
   
    # An exception will occur as the container class of the subfolder being added (IPF.Note)
    # does not match the container class of the parent folder (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Cambiar la clase de contenedor de una carpeta**
A veces es necesario cambiar la clase de carpeta de una carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En estos casos, es necesario cambiar la clase de carpeta para que todos los elementos de la carpeta se muestren correctamente. El siguiente fragmento de código muestra cómo cambiar la clase contenedora de una carpeta en PST para este fin.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}

## **Agregue mensajes masivos con un rendimiento mejorado**

Agregar mensajes masivos a un archivo PST en lugar de agregarlos individualmente puede ofrecer varias ventajas, especialmente en términos de eficiencia y rendimiento: menos operaciones de E/S, menor tiempo para completar la tarea, utilizar los recursos del sistema de manera más eficiente, etc. *add_messages* método del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) La clase se usa para transferir la colección de mensajes MAPI obtenidos de la carpeta de origen a la carpeta de destino.

### **Agregar mensajes de otro PST**

Para enumerar y recuperar todos los mensajes MAPI de la carpeta de origen de un archivo PST, utilice *enumerate_mapi_messages()* método del [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) clase. A continuación, añada estos mensajes a la carpeta de destino de otro archivo PST.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Get the folder by name
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Agregar mensajes desde el directorio**

Para agregar mensajes desde el directorio, después de abrir el archivo y obtener la referencia a una carpeta específica dentro del archivo PST, recupere una lista de nombres de archivos de un directorio especificado por la variable «path» y cree una lista MSG vacía para cargar cada archivo como un mapiMessage. Añada cada mensaje cargado a la msg_list. El siguiente ejemplo de código muestra el proceso de agregar mensajes desde el directorio:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Get the folder by name
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```