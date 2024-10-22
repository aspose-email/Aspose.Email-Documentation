---
title: "Trabajando con MapiNote en PST"
url: /es/net/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Añadiendo MapiNote a PST**

El artículo [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) a la subcarpeta de Notas de un archivo PST que has creado o cargado. Para agregar un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) a un PST:

1. Crea una plantilla de [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) usando Microsoft Outlook y guárdala como un archivo MSG.
2. Carga la nota MSG guardada en un objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
3. Crea un objeto [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) y carga la nota MSG plantilla.
4. Establece las [propiedades de MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Crea un PST usando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
6. Crea una carpeta predefinida (Notas) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

El siguiente fragmento de código te muestra cómo crear un [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) y luego agregarlo a la carpeta de notas de un archivo PST recién creado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}