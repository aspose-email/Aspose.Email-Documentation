---
title: "Trabajando con MapiJournal en PST"
url: /es/java/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Agregar MapiJournal a PST**

[Crear un nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar MapiJournal a la subcarpeta Journal de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiJournal a un PST:

1. Crea un [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) object.
1. Configure el [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) propiedades que utilizan un constructor y métodos.
1. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Cree una carpeta predefinida (Diarios) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

El siguiente fragmento de código muestra cómo crear un [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) y, a continuación, agréguelo a la carpeta Journal de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}

## **Agregar archivos adjuntos a MapiJournal**

También es posible agregar archivos adjuntos a los elementos del diario MAPI. El siguiente código muestra cómo hacerlo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}
