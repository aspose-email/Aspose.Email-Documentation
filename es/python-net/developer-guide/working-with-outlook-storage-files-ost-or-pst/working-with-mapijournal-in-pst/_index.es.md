---
title: "Trabajando con MapiJournal en PST"
url: /es/python-net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Añadiendo MapiJournal a PST**
Crear un nuevo archivo PST y añadir subcarpetas mostró cómo crear un archivo PST y añadirle una subcarpeta. Con Aspose.Email puedes añadir MapiJournal a la subcarpeta de Journal de un archivo PST que has creado o cargado. A continuación se presentan los pasos para añadir MapiJournal a un PST:

1. Crea un objeto MapiJournal
1. Establece las propiedades de MapiJournal utilizando un constructor y métodos.
1. Crea un PST usando el método PersonalStorage.create().
1. Crea una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método add_mapi_message_item().

El siguiente fragmento de código muestra cómo crear un MapiJournal y luego añadirlo a la carpeta de journal de un archivo PST recién creado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}
## **Añadiendo adjuntos a MapiJournal**
El siguiente fragmento de código muestra cómo añadir adjuntos a MapiJournal.

```py
import os
from datetime import datetime, timedelta
from aspose.email.mapi import MapiJournal

data_dir = "path_to_data_directory"
attach_file_names = [os.path.join(data_dir, "Desert.jpg"), os.path.join(data_dir, "download.png")]

journal = MapiJournal("testJournal", "This is a test journal", "Phone call", "Phone call")
journal.start_time = datetime.now()
journal.end_time = journal.start_time + timedelta(hours=1)
journal.companies = ["company 1", "company 2", "company 3"]

for attach in attach_file_names:
    journal.attachments.append(attach, open(attach, 'rb').read())

journal.save(os.path.join(data_dir, "AddAttachmentsToMapiJournal_out.msg"))
```