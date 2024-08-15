---
title: "Trabajando con MapiTask en PST"
url: /es/python-net/working-with-mapitask-in-pst/
weight: 90
type: docs
---


## **Agregar MapiTask a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes añadir MapiTask a la subcarpeta Tareas de un archivo PST que hayas creado o cargado. A continuación se detallan los pasos para agregar MapiTask a un PST:

1. Cree un objeto MapiTask.
1. Establezca las propiedades de MapiTask utilizando el constructor y diferentes métodos.
1. Cree un PST con el método PersonalStorage.create ().
1. Cree una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método addMapIMessageItem ().

El siguiente fragmento de código muestra cómo crear un MapiTask y, a continuación, añadirlo a la carpeta de tareas de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}
