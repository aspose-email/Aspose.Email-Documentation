---
title: "Convertir OLM a PST"
url: /es/python-net/convert-olm-to-pst/
weight: 90
type: docs
---


## **Convertir OLM a PST**

OLM (Outlook para Mac) es un formato de archivo utilizado por Microsoft Outlook para Mac para almacenar mensajes de correo electrónico, contactos, calendarios, tareas y otros datos. Es el formato de archivo nativo de Outlook para Mac, por lo que no es posible abrir un archivo de Outlook para Mac (OLM) en Outlook para Windows. Para trabajar con archivos OLM en Windows, Aspose Email proporciona herramientas diseñadas específicamente para gestionar archivos OLM. Su enfoque consiste en convertir archivos OLM al formato PST (archivo de datos de Outlook), que es ampliamente compatible en entornos Windows. Una vez convertidos al formato PST, puede importar los datos a Outlook para Windows o a cualquier otro cliente de correo electrónico compatible. El siguiente ejemplo de código le mostrará cómo convertir un OLM en un PST.

**Migración de datos de correo electrónico del formato OLM al formato PST**

```py

import aspose.email as ae

# create an instance of OlmStorage class to open source OLM
olm = ae.storage.olm.OlmStorage("my.olm")
# create a new PST file
pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

# recursively reads each folder and its messages
# and adds them to the PST in the same order

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```
**Implementación de 'get_container_class' para categorizar diferentes tipos de elementos de Outlook**

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