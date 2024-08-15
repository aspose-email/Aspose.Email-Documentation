---
title: "Прочитайте PST в хранилище Outlook"
url: /ru/java/read-outlook-storage-pst/
weight: 30
type: docs
---

## **Aspose.Email - чтение PST в хранилище Outlook**
Файл Outlook PST можно загрузить в экземпляр [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) class.

**Java**

``` java

 // Load the Outlook PST file

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Get the Display Name of the PST file

System.out.println("Display Name: " + pst.getDisplayName());


```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
