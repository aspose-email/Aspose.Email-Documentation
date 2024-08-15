---
title: "Trabajando con MapiNote en PST"
url: /es/net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Añadir MapiNote a PST**

The [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) El artículo muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) a la subcarpeta Notas de un archivo PST que haya creado o cargado. Para añadir un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) a un PST:

1. Crear una plantilla [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) usando Microsoft Outlook y guárdalo como un archivo MSG.
2. Cargue la nota MSG guardada en un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
3. Crea un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) objeta y carga la nota MSG de la plantilla.
4. Configure el [Propiedades de MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
6. Cree una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

El siguiente fragmento de código muestra cómo crear un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) y, a continuación, agréguelo a la carpeta de notas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}
