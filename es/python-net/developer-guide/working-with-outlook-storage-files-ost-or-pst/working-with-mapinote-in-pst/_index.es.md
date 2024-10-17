---
title: "Trabajando con MapiNote en PST"
url: /es/python-net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Añadiendo MapiNote a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un MapiNote a la subcarpeta de Notas de un archivo PST que hayas creado o cargado. Para agregar un MapiNote a un PST:

1. Crea un MapiNote de plantilla utilizando Microsoft Outlook y guárdalo como un archivo MSG.
1. Carga la nota MSG guardada en un objeto MapiMessage.
1. Crea un objeto MapiNote y carga la nota MSG de plantilla.
1. Establece las propiedades de MapiNote.
1. Crea un PST utilizando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código te muestra cómo crear un MapiNote y luego agregarlo a la carpeta de notas de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}