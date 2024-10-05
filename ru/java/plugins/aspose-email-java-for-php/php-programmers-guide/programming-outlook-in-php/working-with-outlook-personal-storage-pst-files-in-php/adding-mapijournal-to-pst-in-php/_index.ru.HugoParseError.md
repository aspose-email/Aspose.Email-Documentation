---
title: Добавление MapiJournal в PST на PHP
type: docs
weight: 40
url: /java/adding-mapijournal-to-pst-in-php/
---

## **Aspose.Email - Добавление MapiJournal в PST**
Чтобы добавить MapiJournal в PST с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **AddMapiJournalToPST**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 $d1 = new Date();

$calendar=new Calendar();

$cl = $calendar->getInstance();

$cl->setTime($d1);

$cl->add($calendar->HOUR, 1);

$d2 = $cl->getTime();

$journal = new MapiJournal("ежедневная запись", "вызываемый в темноте", "Телефонный звонок", "Телефонный звонок");

$journal->setStartTime($d1);

$journal->setEndTime($d2);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "JournalPST.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$journal_folder = $pst->createPredefinedFolder("Журнал", $standardIpmFolder->Journal);

$journal_folder->addMapiMessageItem($journal);

print "MapiJournal успешно добавлен.".PHP_EOL;

```
## **Скачать исполняемый код**
Скачайте **Добавление MapiJournal в PST (Aspose.Email)** с любого из указанных ниже социальных сайтов кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)