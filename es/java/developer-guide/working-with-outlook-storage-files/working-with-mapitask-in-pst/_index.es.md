---
title: "Trabajando con MapiTask en PST"
url: /es/java/working-with-mapitask-in-pst/
weight: 60
type: docs
---

## **Agregar MapiTask a PST**

[Crear un nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir MapiTask a la subcarpeta Tareas de un archivo PST que hayas creado o cargado.

A continuación se detallan los pasos para agregar MapiTask a un PST:

1. Crea un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) object.
1. Configure el [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) propiedades que utilizan el constructor y diferentes métodos.
1. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Cree una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

El siguiente fragmento de código muestra cómo crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) y, a continuación, agréguelo a la carpeta Tareas de un archivo PST recién creado.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiTaskToPST-.java" >}}
