---
title: "Добавление файлов в PST в PHP"
url: /ru/java/adding-files-to-pst-in-php/
weight: 10
type: docs
---

## **Aspose.Email - добавление файлов в PST**
Чтобы добавить файл в PST, используя **Aspose.Электронная почта Java для PHP**, просто вызовите **AddFileToPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Добавление файлов в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST.php)
