---
title: Чтение Outlook PST и получение информации о папках и подпапках
type: docs
weight: 20
url: /java/read-outlook-pst-and-get-folders-and-subfolders-information/
---

## **Aspose.Email - Чтение Outlook PST и получение информации о папках и подпапках**
Aspose.Email для Java позволяет вам читать файлы PST Microsoft Outlook. Вы можете загрузить файл PST с диска или потока в экземпляр класса [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) и получить информацию о его содержимом, например папки, подпапки и сообщения.

После загрузки файла PST в класс [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) вы можете получить информацию о имени файла для отображения, корневой папке, количестве подпапок и сообщениях.

**Java**

```java

 // Загрузить файл Outlook PST

PersonalStorage pst = PersonalStorage.fromFile(dataDir + "personalStorage.pst");

// Получить имя для отображения файла PST

System.out.println("Имя для отображения: " + pst.getDisplayName());

// Получить информацию о папках

FolderInfoCollection folderInfoCollection = pst.getRootFolder().getSubFolders();

// Перебрать каждую папку, чтобы отобразить имя папки и количество сообщений

for (int i = 0; i < folderInfoCollection.size(); i++)

{

    FolderInfo folderInfo = (FolderInfo) folderInfoCollection.get_Item(i);

    System.out.println("Папка: " + folderInfo.getDisplayName());

    System.out.println("Всего элементов: " + folderInfo.getContentCount());

    System.out.println("Всего непрочитанных элементов: " + folderInfo.getContentUnreadCount());

    System.out.println("-----------------------------------");

}

```
## **Скачать работающий код**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}} 

Для получения более подробной информации посетите [Чтение файла Outlook PST и получение информации о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}