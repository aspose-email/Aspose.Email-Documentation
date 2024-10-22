---
title: "Convertir OLM a PST"
url: /es/python-net/convert-olm-to-pst/
weight: 90
type: docs
---


## **Convertir OLM a PST**

OLM (Outlook para Mac) es un formato de archivo utilizado por Microsoft Outlook para Mac para almacenar mensajes de correo electrónico, contactos, calendarios, tareas y otros datos. Es el formato de archivo nativo para Outlook para Mac, por lo que no es posible abrir un archivo de Outlook para Mac (OLM) en Outlook para Windows. Para trabajar con archivos OLM en Windows, Aspose Email proporciona herramientas específicamente diseñadas para manejar archivos OLM. Su enfoque es convertir archivos OLM al formato PST (Archivo de Datos de Outlook), que es ampliamente compatible en entornos de Windows. Una vez convertido al formato PST, puedes importar los datos a Outlook para Windows o a cualquier otro cliente de correo electrónico compatible. El siguiente ejemplo de código te mostrará cómo convertir un OLM a un PST.

**Migración de datos de correo electrónico de OLM a formato PST**

```py

import aspose.email as ae

# crea una instancia de la clase OlmStorage para abrir el OLM fuente
olm = ae.storage.olm.OlmStorage("my.olm")
# crea un nuevo archivo PST
pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

# lee recursivamente cada carpeta y sus mensajes
# y los añade al PST en el mismo orden

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```
**Implementación de 'get_container_class' para clasificar diferentes tipos de elementos de Outlook**

```py
def get_container_class(message_class):
    if message_class.startswith("IPM.Contact") or message_class.startswith("IPM.DistList"):
        return "IPF.Contact"

    if message_class.startswith("IPM.StickyNote"):
        return "IPF.StickyNote"

    if message_class.startswith("IPM.Activity"):
        return "IPF.Journal"

    if message_class.startswith("IPM.Task"):
        return "IPF.Task"

    if message_class.startswith("IPM.Appointment") or message_class.startswith("IPM.Schedule.meeting"):
        return "IPF.Appointment"

    return "IPF.Note"
```
**Implementación de la función 'add_to_pst' para transferir datos de un archivo OLM a un archivo PST**

```py

def add_to_pst(pst_folder, olm_folder):
    pst_sub_folder = pst_folder.get_sub_folder(olm_folder.name)

    for msg in olm_folder.enumerate_mapi_messages():
        if pst_sub_folder is None:
            pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name, get_container_class(msg.message_class))

        pst_sub_folder.add_message(msg)

    if pst_sub_folder is None:
        pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name)

    for olm_sub_folder in olm_folder.sub_folders:
        add_to_pst(pst_sub_folder, olm_sub_folder)
```