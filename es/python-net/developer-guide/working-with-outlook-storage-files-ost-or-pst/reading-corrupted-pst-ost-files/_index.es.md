---
title: "Lectura de archivos PST/OST corruptos"
url: /es/python-net/reading-corrupted-pst-ost-files/
weight: 90
type: docs
---


## **Lectura de archivos PST/OST corruptos**

A veces puede no ser posible abrir un archivo PST debido a algunos problemas. Uno de esos problemas es la corrupción del archivo. Si un archivo PST está dañado o corrupto, puede que no sea posible abrirlo utilizando el cliente de correo Outlook. Aspose.Email proporciona una API diseñada para escanear un archivo PST dañado y leer los mensajes no dañados dentro de un archivo por sus IDs.

Los siguientes métodos de la clase [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) son esenciales para afrontar estas tareas:

Para obtener la lista de IDs:

- **find_messages(parent_entry_id)** - recupera una lista de IDs de mensajes dentro de una carpeta específica.

- **find_subfolders(parent_entry_id)** - obtiene una lista de IDs de subcarpetas dentro de la carpeta raíz.

Para usar estos IDs y obtener el contenido del archivo:

- **extract_message(entry_id)** - intenta recuperar un mensaje.

- **get_folder_by_id(entry_id)** - accede a cada carpeta.

El siguiente ejemplo de código demuestra cómo explorar y acceder al contenido de un archivo PST potencialmente corrupto:

```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Error al leer el mensaje. ID de entrada: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Error al leer el mensaje. ID de entrada: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```