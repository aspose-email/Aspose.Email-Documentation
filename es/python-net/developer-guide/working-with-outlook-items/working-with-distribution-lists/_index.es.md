---
title: "Trabajando con Listas de Distribución"
url: /es/python-net/working-with-distribution-lists/
weight: 40
type: docs
---


Es posible crear una lista de distribución utilizando la API de Aspose.Email, que es una colección de múltiples contactos. Una lista de distribución se puede guardar en disco en formato MSG de Outlook y se puede ver/manipular abriéndola en MS Outlook.
## **Creando y Guardando una Lista de Distribución**
El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}

## **Leyendo una Lista de Distribución de un PST**

El siguiente fragmento de código muestra cómo leer una lista de distribución de un archivo PST.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file( "your_pst_file.pst")
folder = pst.root_folder.get_sub_folder("Contacts")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    dlist = msg.to_mapi_message_item()
    if isinstance(dlist, ae.mapi.MapiDistributionList):
        for member in dlist.members:
            print("Nombre para Mostrar del Miembro:", member.display_name)
            print("Dirección de Correo Electrónico del Miembro:", member.email_address)
```