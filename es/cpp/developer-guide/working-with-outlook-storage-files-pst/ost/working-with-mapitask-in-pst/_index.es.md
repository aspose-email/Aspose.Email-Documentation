---
title: "Trabajando con MapiTask en PST"
url: /es/cpp/working-with-mapitask-in-pst/
weight: 90
type: docs
---

## **Agregar MapiTask a PST**
Con Aspose.Email puede agregar MapiTask a la subcarpeta Tareas de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiTask a un PST:

1. Cree un objeto MapiTask.
1. Establezca las propiedades de MapiTask utilizando el constructor y diferentes métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiTask y, a continuación, añadirlo a la carpeta de tareas de un archivo PST recién creado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}
