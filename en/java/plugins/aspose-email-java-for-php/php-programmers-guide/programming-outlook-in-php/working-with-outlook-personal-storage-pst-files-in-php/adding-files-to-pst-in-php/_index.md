---
title: Adding Files to PST in PHP
ArticleTitle: Adding Files to PST in PHP
type: docs
weight: 10
url: /java/adding-files-to-pst-in-php/
---

## **Aspose.Email - Adding Files to PST**
To Add File to PST using **Aspose.Email Java for PHP**, simply invoke **AddFileToPST** module. Here you can see example code.

**PHP Code**

``` php

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "AddFile1.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$fi->addFile($dataDir . "Report.xlsx", "IPM.Document.Excel.Sheet.8");

$pst->dispose();

print "Added file to PST".PHP_EOL;

```
## **Download Running Code**
Download **Adding Files to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
