---
title: "Crear nuevo archivo PST y agregar subcarpetas"
url: /es/python-net/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---

Al igual que el análisis de un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo demuestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. Creando un nuevo archivo PST.
1. Cambiando la clase contenedor de una carpeta.

Utilice la clase PersonalStorage para crear un archivo PST en alguna ubicación de un disco local. Para crear un archivo PST desde cero:

1. Cree un PST utilizando el método PersonalStorage.Create().
1. Agregue una subcarpeta en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddSubFolder.

El siguiente fragmento de código le muestra cómo crear un archivo PST y agregar una subcarpeta llamada Bandeja de entrada.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}
```

## **Verificación de coincidencia de clase contenedor al agregar una carpeta a PST**

Aspose.Email para Python ofrece una solución que mejora el proceso de validación durante la creación de carpetas en archivos PST. Con la propiedad 'EnforceContainerClassMatching' de la clase [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class), puede asegurar una coincidencia estricta de las clases contenedor al agregar una nueva carpeta al almacenamiento PST. Esta característica ayuda a mantener la jerarquía organizativa dentro del archivo PST al prevenir desajustes en las clases contenedor. Al establecer 'EnforceContainerClassMatching' en 'true', se lanzará una excepción si las clases contenedor de las carpetas padre e hija no coinciden, lo que proporciona una protección contra estructuras de carpetas incorrectas. El comportamiento predeterminado de esta propiedad es 'false', permitiendo flexibilidad en la creación de carpetas mientras que le permite hacer cumplir una coincidencia estricta de clases contenedor cuando sea necesario.

El siguiente ejemplo de código demuestra el uso de la propiedad 'EnforceContainerClassMatching' para controlar si se debe lanzar una excepción al agregar carpetas con clases contenedor desajustadas:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
    
    # No se producirá una excepción. EnforceContainerClassMatching es False por defecto.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
    
    # Ocurrirá una excepción ya que la clase contenedor de la subcarpeta agregada (IPF.Note)
    # no coincide con la clase contenedor de la carpeta padre (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Cambiando la clase contenedor de una carpeta**
A veces es necesario cambiar la clase de una carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En tales casos, la clase de la carpeta necesita cambiarse para que todos los elementos en la carpeta se muestren correctamente. El siguiente fragmento de código le muestra cómo cambiar la clase contenedor de una carpeta en PST para este propósito.

```python
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}
```

## **Agregar mensajes en bloque con un rendimiento mejorado**

Agregar mensajes en bloque a un archivo PST, en lugar de agregarlos individualmente, puede ofrecer varias ventajas, particularmente en términos de eficiencia y rendimiento: menos operaciones de E/S, menor tiempo para completar la tarea, los recursos del sistema se utilizan de manera más eficiente, etc. El método *add_messages* de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) se utiliza para transferir la colección de mensajes MAPI obtenidos de la carpeta de origen a la carpeta de destino.

### **Agregar mensajes desde otro PST**

Para enumerar y recuperar todos los mensajes MAPI de la carpeta de origen de un archivo PST, utilice el método *enumerate_mapi_messages()* de la clase [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Luego, agregue estos mensajes a la carpeta de destino de otro archivo PST.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Obtener la carpeta por nombre
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Agregar mensajes desde un directorio**

Para agregar mensajes desde un directorio, después de abrir el archivo y obtener la referencia a una carpeta específica dentro del archivo PST, recupere una lista de nombres de archivos de un directorio especificado por la variable "path" y cree una lista MSG vacía para cargar cada archivo como un MapiMessage. Añada cada mensaje cargado a la msg_list. El siguiente ejemplo de código demuestra el proceso de agregar mensajes desde un directorio:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Obtener la carpeta por nombre
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```