---
title: "Trabajando con MapiTask en PST"
url: /es/python-net/working-with-mapitask-in-pst/
weight: 90
type: docs
---


## **Agregar MapiTask a PST**
Crear un nuevo archivo PST y agregar subcarpetas mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar MapiTask a la subcarpeta Tareas de un archivo PST que has creado o cargado. A continuación se detallan los pasos para agregar MapiTask a un PST:

1. Crea un objeto MapiTask.
1. Establece las propiedades de MapiTask utilizando el constructor y diferentes métodos.
1. Crea un PST usando el método PersonalStorage.Create().
1. Crea una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta Raíz y luego llamando al método AddMapiMessageItem().

El siguiente fragmento de código muestra cómo crear un MapiTask y luego añadirlo a la carpeta de tareas de un archivo PST recién creado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}