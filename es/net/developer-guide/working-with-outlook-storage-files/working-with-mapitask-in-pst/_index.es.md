---
title: "Trabajando con MapiTask en PST"
url: /es/net/working-with-mapitask-in-pst/
weight: 60
type: docs
---


## **Agregar MapiTask a PST**

The [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) El artículo muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) a la subcarpeta Tareas de un archivo PST que haya creado o cargado. A continuación se indican los pasos para añadir MapiTask a un PST:

1. Crea un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) object.
2. Configure el [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) propiedades que utilizan el constructor y diferentes métodos.
3. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Cree una carpeta predefinida (Tareas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

El siguiente fragmento de código muestra cómo crear un [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) y, a continuación, agréguelo a la carpeta de tareas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}
