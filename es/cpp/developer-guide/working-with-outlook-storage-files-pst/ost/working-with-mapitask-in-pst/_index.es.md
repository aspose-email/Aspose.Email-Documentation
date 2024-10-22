---
title: "Trabajando con MapiTask en PST"
url: /es/cpp/working-with-mapitask-in-pst/
weight: 90
type: docs
---

## **Agregar MapiTask a PST**
Con Aspose.Email puedes agregar MapiTask a la subcarpeta de Tareas de un archivo PST que has creado o cargado. A continuación, se presentan los pasos para agregar MapiTask a un PST:

1. Crea un objeto MapiTask.
1. Establece las propiedades de MapiTask utilizando el constructor y diferentes métodos.
1. Crea un PST utilizando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta Raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código muestra cómo crear un MapiTask y luego agregarlo a la carpeta de tareas de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}