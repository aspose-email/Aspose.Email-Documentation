---
title: "Trabajando con MapiJournal en PST"
url: /es/cpp/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Agregar MapiJournal a PST**
Con Aspose.Email puede agregar MapiJournal a la subcarpeta Journal de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiJournal a un PST:

1. Crear un objeto MapiJournal
1. Establezca las propiedades de MapiJournal mediante un constructor y métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiJournal y, a continuación, añadirlo a la carpeta journal de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}
## **Agregar archivos adjuntos a MapiJournal**
El siguiente fragmento de código muestra cómo agregar archivos adjuntos a MapiJournal.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}
