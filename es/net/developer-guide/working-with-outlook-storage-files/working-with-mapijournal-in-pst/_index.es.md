---
title: "Trabajando con MapiJournal en PST"
url: /es/net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Añadiendo MapiJournal a PST**

El artículo [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) a la subcarpeta Journal de un archivo PST que has creado o cargado. A continuación se presentan los pasos para añadir [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) a un PST:

1. Crear un objeto [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/)
2. Establecer las propiedades de [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) utilizando un constructor y métodos.
3. Crear un PST utilizando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crear una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

El siguiente fragmento de código te muestra cómo crear un [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) y luego añadirlo a la carpeta de journal de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Añadiendo archivos adjuntos a MapiJournal**

El siguiente fragmento de código te muestra cómo añadir archivos adjuntos a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}