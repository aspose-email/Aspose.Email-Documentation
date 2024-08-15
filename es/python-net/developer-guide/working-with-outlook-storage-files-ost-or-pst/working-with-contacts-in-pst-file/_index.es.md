---
title: "Trabajar con contactos en un archivo PST"
url: /es/python-net/working-with-contacts-in-pst-file/
weight: 60
type: docs
---


## **Agregar un contacto a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar un MapiContact a la subcarpeta Contactos de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiContact a un PST:

1. Cree un objeto MapiContact.
1. Establezca las propiedades de MapiContact con diferentes constructores y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método add_mapi_message_item ().

El siguiente fragmento de código muestra cómo crear un MapiContact y, a continuación, añadirlo a la carpeta de contactos de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}
## **Guarde la información de contactos del archivo PST en formato MSG**
En este artículo se explica cómo acceder a la información de contacto desde un archivo PST de Outlook y guardar el contacto en el disco en formato MSG. Las clases PersonalStorage y MapiContact para obtener y mostrar la información de contacto. Los pasos para obtener la información de contacto son:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al método PersonalStorage.extract_message () para obtener la información de contacto de la clase MAPIMessage.
1. Llame al método mapiMessage.save () para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código muestra cómo recuperar toda la información de contacto del archivo PST y guardarla en el disco en formato MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}
## **Guarde la información de contactos del archivo PST en formato VCF**
Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar el contacto en un disco en formato vCard (VCF). Utilice las clases PersonalStorage y MapiContact para obtener la información de contacto del archivo PST. Para obtener la información de contacto:

1. Cargue el archivo PST en la clase PersonalStorage.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos para obtener la colección de mensajes.
1. Recorre la colección de mensajes.
1. Llame al método PersonalStorage.extract_message () para obtener la información de contacto de la clase MAPIContact.
1. Utilice las diferentes propiedades de la clase MapiContact para acceder a la información de contacto.

El siguiente programa carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de contactos vCard estándar. Si abres cualquier archivo VCF en Microsoft Outlook, tendrá el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar contactos del formato PST de Outlook al formato vCard (VCF).



```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Load the Outlook PST file
pst = PersonalStorage.from_file("my.pst")

# Get the Contacts folder
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Loop through all the contacts in this folder
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Get the contact information
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Display some contents on screen
    print("Name: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Save to disk in vCard VCF format
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```
## **Trabajando con listas de distribución**
Es posible crear una lista de distribución utilizando la API Aspose.Email que es una colección de varios contactos. Una lista de distribución se puede guardar en un disco en formato MSG de Outlook y se puede ver o manipular abriéndola en MS Outlook.
### **Creación y almacenamiento de una lista de distribución**
El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}
### **Lectura de una lista de distribución desde un PST**
El siguiente fragmento de código muestra cómo leer una lista de distribución desde un PST.

```py
from aspose.email.mapi import MapiMessage

# Load the MAPI message from file
message = MapiMessage.load("dl.msg")

# Convert the message to MAPI distribution list
dlist = message.to_mapi_message_item()
```
