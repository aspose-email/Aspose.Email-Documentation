---
title: "Lea PST de Outlook y obtenga información sobre carpetas y subcarpetas"
url: /es/java/read-outlook-pst-and-get-folders-and-subfolders-information/
weight: 20
type: docs
---

## **Aspose.Email: lea el PST de Outlook y obtenga información sobre carpetas y subcarpetas**
Aspose.Email para Java permite leer archivos PST de Microsoft Outlook. Puede cargar un archivo PST desde un disco o transmitirlo a una instancia del [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) clase y obtenga la información sobre su contenido, por ejemplo, carpetas, subcarpetas y mensajes.

Tras cargar el archivo PST en [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) clase, puede obtener la información sobre el nombre para mostrar del archivo, la carpeta raíz, las subcarpetas y el recuento de mensajes.

**Java**

```java

 // Load the Outlook PST file

PersonalStorage pst = PersonalStorage.fromFile(dataDir + "personalStorage.pst");

// Get the Display Name of the PST file

System.out.println("Display Name: " + pst.getDisplayName());

// Get the folders information

FolderInfoCollection folderInfoCollection = pst.getRootFolder().getSubFolders();

// Browse through each folder to display folder name and number of messages

for (int i = 0; i < folderInfoCollection.size(); i++)

{

    FolderInfo folderInfo = (FolderInfo) folderInfoCollection.get_Item(i);

    System.out.println("Folder: " + folderInfo.getDisplayName());

    System.out.println("Total items: " + folderInfo.getContentCount());

    System.out.println("Total unread items: " + folderInfo.getContentUnreadCount());

    System.out.println("-----------------------------------");

}

```
## **Descargar Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
