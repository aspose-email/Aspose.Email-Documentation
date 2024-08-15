---
title: "Lectura de archivos PST/OST corruptos"
url: /es/python-net/reading-corrupted-pst-ost-files/
weight: 90
type: docs
---


## **Lectura de archivos PST/OST corruptos**

A veces, puede que no sea posible abrir un archivo PST debido a algunos problemas. Uno de esos problemas es la corrupción del archivo. Si un archivo PST está dañado o dañado, es posible que no sea posible abrirlo con el cliente de correo electrónico de Outlook. Aspose.Email proporciona una API diseñada para escanear un archivo PST dañado y leer los mensajes intactos de un archivo según sus ID.

Los siguientes métodos del [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) las clases son esenciales para hacer frente a estas tareas:

Para obtener la lista de identificaciones:

- **find_messages(parent_entry_id)** - recupera una lista de identificadores de mensajes dentro de una carpeta específica.

- **find_subfolders(parent_entry_id)** - obtiene una lista de los ID de subcarpetas de la carpeta raíz.

Para usar estos ID para obtener el contenido del archivo:

- **extract_message(entry_id)** - intenta recuperar un mensaje.

- **get_folder_by_id(entry_id)** - accede a cada carpeta.

El siguiente ejemplo de código muestra cómo explorar y acceder al contenido de un archivo PST que podría estar dañado:

```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Message reading error. Entry id: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Message reading error. Entry id: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```