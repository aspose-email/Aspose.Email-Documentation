---
title: "Trabajando con MapiNote en PST"
url: /es/java/trabajando-con-mapinote-en-pst/
weight: 80
type: docs
---

## **Agregando MapiNote a PST**

[Crear nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar un MapiNote a la subcarpeta de Notas de un archivo PST que hayas creado o cargado.

A continuación se presentan los pasos para agregar MapiNote a un PST:

1. Crea un MapiNote plantilla utilizando Microsoft Outlook y guárdalo como un archivo MSG.
1. Carga la nota MSG guardada en un objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
1. Crea un objeto [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) y carga la nota MSG plantilla.
1. Establece las propiedades del [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) utilizando diferentes métodos.
2. Crea un PST utilizando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) .
3. Crea una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) .

El siguiente fragmento de código muestra cómo crear un [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) y luego agregarlo a la carpeta Notas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}