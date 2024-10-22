---
title: "Leer archivos PST de Outlook y obtener información de carpetas y subcarpetas"
url: /es/java/read-outlook-pst-and-get-folders-and-subfolders-information/
weight: 20
type: docs
---

## **Aspose.Email - Leer archivos PST de Outlook y obtener información de carpetas y subcarpetas**
Aspose.Email para Java te permite leer archivos PST de Microsoft Outlook. Puedes cargar un archivo PST desde el disco o como un flujo en una instancia de la clase [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) y obtener la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

Después de cargar el archivo PST en la clase [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage), puedes obtener la información sobre el nombre de visualización del archivo, la carpeta raíz, las subcarpetas y el conteo de mensajes.

**Java**

```java

 // Cargar el archivo PST de Outlook

PersonalStorage pst = PersonalStorage.fromFile(dataDir + "personalStorage.pst");
  
// Obtener el nombre de visualización del archivo PST

System.out.println("Nombre de visualización: " + pst.getDisplayName());
  
// Obtener la información de las carpetas

FolderInfoCollection folderInfoCollection = pst.getRootFolder().getSubFolders();
  
// Recorrer cada carpeta para mostrar el nombre de la carpeta y el número de mensajes

for (int i = 0; i < folderInfoCollection.size(); i++)

{

    FolderInfo folderInfo = (FolderInfo) folderInfoCollection.get_Item(i);

    System.out.println("Carpeta: " + folderInfo.getDisplayName());

    System.out.println("Total de elementos: " + folderInfo.getContentCount());

    System.out.println("Total de elementos no leídos: " + folderInfo.getContentUnreadCount());

    System.out.println("-----------------------------------");

}

```
## **Descargar Código en Ejecución**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Leer Archivo PST de Outlook y Obtener Información de Carpetas y Subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}