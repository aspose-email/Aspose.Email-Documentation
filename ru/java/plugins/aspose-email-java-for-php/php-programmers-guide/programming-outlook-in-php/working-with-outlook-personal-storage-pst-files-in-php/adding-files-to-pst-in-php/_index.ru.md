---
title: "Добавление файлов в PST в PHP"
url: /ru/java/adding-files-to-pst-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Добавление файлов в PST**
Чтобы добавить файл в PST с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **AddFileToPST**. Здесь вы можете видеть пример кода.

**PHP код**

``` php

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "AddFile1.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$fi->addFile($dataDir . "Report.xlsx", "IPM.Document.Excel.Sheet.8");

$pst->dispose();

print "Добавлен файл в PST".PHP_EOL;

```
## **Загрузка работающего кода**
Скачайте **Добавление файлов в PST (Aspose.Email)** с любого из указанных ниже сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)