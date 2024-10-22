---
title: "Trabajando con MapiJournal en PST"
url: /es/cpp/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Agregar MapiJournal a PST**
Con Aspose.Email puedes agregar MapiJournal a la subcarpeta Journal de un archivo PST que hayas creado o cargado. A continuación se muestran los pasos para agregar MapiJournal a un PST:

1. Crea un objeto MapiJournal
1. Establece las propiedades de MapiJournal utilizando un constructor y métodos.
1. Crea un PST utilizando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código te muestra cómo crear un MapiJournal y luego agregarlo a la carpeta de diarios de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}
## **Agregar Archivos Adjuntos a MapiJournal**
El siguiente fragmento de código te muestra cómo agregar archivos adjuntos a MapiJournal.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}