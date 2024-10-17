---
title: "Trabajando con MapiTask en PST"
url: /es/java/working-with-mapitask-in-pst/
weight: 60
type: docs
---

## **Añadiendo MapiTask a PST**

[Crear nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar MapiTask a la subcarpeta de Tareas de un archivo PST que hayas creado o cargado.

A continuación, se presentan los pasos para agregar MapiTask a un PST:

1. Crear un objeto [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer las propiedades de [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) utilizando el constructor y diferentes métodos.
1. Crear un PST utilizando el método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
1. Crear una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

El siguiente fragmento de código muestra cómo crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) y luego agregarlo a la carpeta de Tareas de un archivo PST recién creado.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiTaskToPST-.java" >}}
