---
title: "Добавление журнала MapiJournal в PST на PHP"
url: /ru/java/adding-mapijournal-to-pst-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Добавление журнала MapiJournal в PST**
Чтобы добавить MapiJournal в PST, используя **Aspose.Электронная почта Java для PHP**, просто вызовите **AddMapiJournalToPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

``` php

 $d1 = new Date();

$calendar=new Calendar();

$cl = $calendar->getInstance();

$cl->setTime($d1);

$cl->add($calendar->HOUR, 1);

$d2 = $cl->getTime();

$journal = new MapiJournal("daily record", "called out in the dark", "Phone call", "Phone call");

$journal->setStartTime($d1);

$journal->setEndTime($d2);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "JournalPST.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$journal_folder = $pst->createPredefinedFolder("Journal", $standardIpmFolder->Journal);

$journal_folder->addMapiMessageItem($journal);

print "Added MapiJournal Successfully.".PHP_EOL;

```
## **Загрузить рабочий код**
Download **Добавление журнала MAPIjournal в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
