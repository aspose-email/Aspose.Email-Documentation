---
title: "Trabajando con MapiNote en PST"
url: /es/cpp/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Agregando MapiNote a PST**
Con Aspose.Email, puedes agregar un MapiNote a la subcarpeta de Notas de un archivo PST que hayas creado o cargado. Para agregar un MapiNote a un PST:

1. Crea un MapiNote de plantilla usando Microsoft Outlook y guárdalo como un archivo MSG.
1. Carga la nota MSG guardada en un objeto MapiMessage.
1. Crea un objeto MapiNote y carga la nota MSG de plantilla.
1. Establece las propiedades del MapiNote.
1. Crea un PST usando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código te muestra cómo crear un MapiNote y luego agregarlo a la carpeta de notas de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cpp" >}}