---
title: "Чтение Outlook PST и получение информации о папках и подпапках"
url: /ru/java/read-outlook-pst-and-get-folders-and-subfolders-information/
weight: 20
type: docs
---

## **Aspose.Email - чтение Outlook PST и получение информации о папках и подпапках**
Aspose.Email для Java позволяет читать файлы Microsoft Outlook PST. Вы можете загрузить файл PST с диска или в потоковом режиме в экземпляр [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях.

После загрузки файла PST в [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) класс, вы можете получить информацию о отображаемом имени файла, корневой папке, подпапках и количестве сообщений.

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
## **Загрузить рабочий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
