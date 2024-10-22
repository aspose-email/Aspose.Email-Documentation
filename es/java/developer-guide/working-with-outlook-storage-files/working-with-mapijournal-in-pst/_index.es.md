---
title: "Trabajando con MapiJournal en PST"
url: /es/java/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Agregando MapiJournal a PST**

[Crear nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar MapiJournal a la subcarpeta Journal de un archivo PST que has creado o cargado. A continuación se presentan los pasos para agregar MapiJournal a un PST:

1. Crea un objeto [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/).
1. Establece las propiedades del [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) usando un constructor y métodos.
1. Crea un PST usando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
1. Crea una carpeta predefinida (Journals) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

El fragmento de código a continuación muestra cómo crear un [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) y luego agregarlo a la carpeta Journal de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}

## **Agregando archivos adjuntos a MapiJournal**

También es posible agregar archivos adjuntos a los elementos del diario MAPI. El código a continuación muestra cómo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}