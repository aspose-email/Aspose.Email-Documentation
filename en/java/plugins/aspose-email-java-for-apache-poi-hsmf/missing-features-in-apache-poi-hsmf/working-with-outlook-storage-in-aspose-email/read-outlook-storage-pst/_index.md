---
title: Read Outlook Storage PST
type: docs
weight: 30
url: /java/read-outlook-storage-pst/
---

## **Aspose.Email - Read Outlook Storage PST**
An Outlook PST file can be loaded into an instance of the [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) class.

**Java**

``` java

 // Load the Outlook PST file

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Get the Display Name of the PST file

System.out.println("Display Name: " + pst.getDisplayName());


```
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}} 

For more details, visit [Read Outlook PST File and Get Folders and Subfolders Information](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
