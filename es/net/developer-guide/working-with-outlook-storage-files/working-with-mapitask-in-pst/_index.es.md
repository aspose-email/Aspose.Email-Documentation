---
title: "Trabajando con MapiTask en PST"
url: /es/net/working-with-mapitask-in-pst/
weight: 60
type: docs
---


## **Añadiendo MapiTask a PST**

El artículo [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) a la subcarpeta de Tareas de un archivo PST que hayas creado o cargado. A continuación se presentan los pasos para agregar MapiTask a un PST:

1. Crear un objeto [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).
2. Establecer las propiedades del [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) utilizando el constructor y diferentes métodos.
3. Crear un PST utilizando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crear una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

El siguiente fragmento de código muestra cómo crear un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) y luego agregarlo a la carpeta de tareas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}