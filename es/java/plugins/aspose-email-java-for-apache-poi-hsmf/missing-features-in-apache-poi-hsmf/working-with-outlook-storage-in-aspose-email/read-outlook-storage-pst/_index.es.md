---
title: "Lea Outlook Storage PST"
url: /es/java/read-outlook-storage-pst/
weight: 30
type: docs
---

## **Aspose.Email - Lea el PST de Outlook Storage**
Se puede cargar un archivo PST de Outlook en una instancia de [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) class.

**Java**

``` java

 // Load the Outlook PST file

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Get the Display Name of the PST file

System.out.println("Display Name: " + pst.getDisplayName());


```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Lea el archivo PST de Outlook y obtenga información sobre carpetas y subcarpetas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
