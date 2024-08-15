---
title: "Trabajando con MapiNote en PST"
url: /es/python-net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Añadir MapiNote a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar un MapiNote a la subcarpeta Notes de un archivo PST que haya creado o cargado. Para añadir un MapiNote a un PST:

1. Cree una plantilla MapiNote con Microsoft Outlook y guárdela como un archivo MSG.
1. Carga la nota MSG guardada en un objeto MapiMessage.
1. Cree un objeto MapiNote y cargue la nota MSG de plantilla.
1. Establezca las propiedades de MapiNote.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Notes) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiNote y, a continuación, añadirlo a la carpeta de notas de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}
