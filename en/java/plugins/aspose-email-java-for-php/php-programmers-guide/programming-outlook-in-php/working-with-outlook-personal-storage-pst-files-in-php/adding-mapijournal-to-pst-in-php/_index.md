---
title: Adding MapiJournal to PST in PHP
type: docs
weight: 40
url: /java/adding-mapijournal-to-pst-in-php/
---

## **Aspose.Email - Adding MapiJournal to PST**
To Add MapiJournal to PST using **Aspose.Email Java for PHP**, simply invoke **AddMapiJournalToPST** module. Here you can see example code.

**PHP Code**

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
## **Download Running Code**
Download **Adding MapiJournal to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
