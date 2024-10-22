---
title: "Trabajando con contactos en archivos PST"
url: /es/python-net/working-with-contacts-in-pst-file/
weight: 60
type: docs
---


## **Agregar contacto al PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar un MapiContact a la subcarpeta Contactos de un archivo PST que hayas creado o cargado. A continuación se presentan los pasos para agregar un MapiContact a un PST:

1. Crear un objeto MapiContact.
1. Establecer las propiedades del MapiContact utilizando diferentes constructores y métodos.
1. Crear un PST usando el método PersonalStorage.create().
1. Crear una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método add_mapi_message_item().

El siguiente fragmento de código te muestra cómo crear un MapiContact y luego agregarlo a la carpeta de contactos de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}
## **Guardar información de contactos del archivo PST en formato MSG**
Este artículo explica cómo acceder a la información de contacto de un archivo PST de Outlook y guardar el contacto en el disco en formato MSG. Se utilizan las clases PersonalStorage y MapiContact para obtener y mostrar la información del contacto. Los pasos para obtener la información de contacto son:

1. Cargar el archivo PST en la clase PersonalStorage.
1. Navegar por la carpeta de Contactos.
1. Obtener el contenido de la carpeta de Contactos para obtener la colección de mensajes.
1. Recorrer la colección de mensajes.
1. Llamar al método PersonalStorage.extract_message() para obtener la información de contacto en la clase MapiMessage.
1. Llamar al método MapiMessage.save() para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código te muestra cómo recuperar toda la información de contacto del archivo PST y guardarla en el disco en formato MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}
## **Guardar información de contactos del archivo PST en formato VCF**
Este artículo muestra cómo acceder a la información de contacto de un archivo PST de Microsoft Outlook y guardar el contacto en el disco en formato vCard (VCF). Utiliza las clases PersonalStorage y MapiContact para obtener la información del contacto del archivo PST. Para obtener la información del contacto:

1. Cargar el archivo PST en la clase PersonalStorage.
1. Navegar por la carpeta de Contactos.
1. Obtener el contenido de la carpeta de Contactos para obtener la colección de mensajes.
1. Recorrer la colección de mensajes.
1. Llamar al método PersonalStorage.extract_message() para obtener la información de contacto en la clase MapiContact.
1. Utilizar diferentes propiedades de la clase MapiContact para acceder a la información del contacto.

El programa a continuación carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF pueden ser utilizados en cualquier otro programa que pueda cargar el archivo de contacto estándar vCard. Si abres cualquier archivo VCF en Microsoft Outlook, se verá como el de la captura de pantalla a continuación.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código te muestra cómo exportar contactos desde Outlook PST a formato vCard (VCF).



```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Cargar el archivo PST de Outlook
pst = PersonalStorage.from_file("my.pst")

# Obtener la carpeta de Contactos
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Recorrer todos los contactos en esta carpeta
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Obtener la información del contacto
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Mostrar algunos contenidos en pantalla
    print("Nombre: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Guardar en disco en formato vCard VCF
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```
## **Trabajando con listas de distribución**
Es posible crear una lista de distribución utilizando la API de Aspose.Email, que es una colección de múltiples contactos. Una lista de distribución se puede guardar en disco en formato MSG de Outlook y puede ser vista/manipulada abriéndola en MS Outlook.
### **Crear y guardar una lista de distribución**
El siguiente fragmento de código te muestra cómo crear y guardar una lista de distribución.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}
### **Leer una lista de distribución de un PST**
El siguiente fragmento de código te muestra cómo leer una lista de distribución de un PST.

```py
from aspose.email.mapi import MapiMessage

# Cargar el mensaje MAPI desde el archivo
message = MapiMessage.load("dl.msg")

# Convertir el mensaje a una lista de distribución MAPI
dlist = message.to_mapi_message_item()
```