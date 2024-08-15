---
title: "Trabajando con MapiJournal en PST"
url: /es/net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Agregar MapiJournal a PST**

The [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) El artículo muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) a la subcarpeta Journal de un archivo PST que haya creado o cargado. A continuación se indican los pasos para añadirlo [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) a un PST:

1. Crea un [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) object
2. Configure el [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) propiedades que utilizan un constructor y métodos.
3. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Cree una carpeta predefinida (Diarios) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

El siguiente fragmento de código muestra cómo crear un [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) y, a continuación, agréguelo a la carpeta del diario de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Agregar archivos adjuntos a MapiJournal**

El siguiente fragmento de código muestra cómo añadir archivos adjuntos a [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}
