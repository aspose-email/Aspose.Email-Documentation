---
title: Чтение PST-файлов Outlook
type: docs
weight: 30
url: /java/read-outlook-storage-pst/
---

## **Aspose.Email - Чтение PST-файлов Outlook**
PST-файл Outlook может быть загружен в экземпляр класса [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage).

**Java**

``` java

 // Загрузка PST-файла Outlook

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Получение отображаемого имени PST-файла

System.out.println("Отображаемое имя: " + pst.getDisplayName());


```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Чтение PST-файла Outlook и получение информации о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}