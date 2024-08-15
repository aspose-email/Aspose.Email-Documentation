---
title: "Trabajando con MapiJournal en PST"
url: /es/python-net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Agregar MapiJournal a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar MapiJournal a la subcarpeta Journal de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiJournal a un PST:

1. Crear un objeto MapiJournal
1. Establezca las propiedades de MapiJournal mediante un constructor y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método add_mapi_message_item ().

El siguiente fragmento de código muestra cómo crear un MapiJournal y, a continuación, añadirlo a la carpeta journal de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}
## **Agregar archivos adjuntos a MapiJournal**
El siguiente fragmento de código muestra cómo agregar archivos adjuntos a MapiJournal.

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
