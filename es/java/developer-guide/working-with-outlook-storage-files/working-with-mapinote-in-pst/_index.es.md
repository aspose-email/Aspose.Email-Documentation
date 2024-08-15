---
title: "Trabajando con MapiNote en PST"
url: /es/java/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Añadir MapiNote a PST**

[Crear un nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar un MapiNote a la subcarpeta Notes de un archivo PST que haya creado o cargado.

A continuación se indican los pasos para añadir MapiNote a un PST:

1. Cree una plantilla MapiNote con Microsoft Outlook y guárdela como un archivo MSG.
1. Cargue la nota MSG guardada en [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object.
1. Crea un [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) objeta y carga la nota MSG de la plantilla.
1. Configure el [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) propiedades que utilizan diferentes métodos.
2. Cree un PST con el [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
3. Cree una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

El siguiente fragmento de código muestra cómo crear un [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) y, a continuación, agréguelo a la carpeta Notas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}
