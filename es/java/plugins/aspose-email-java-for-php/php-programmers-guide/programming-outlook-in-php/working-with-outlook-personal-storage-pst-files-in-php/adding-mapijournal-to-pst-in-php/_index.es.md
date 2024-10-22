---
title: "Agregar MapiJournal a PST en PHP"
url: /es/java/adding-mapijournal-to-pst-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Agregar MapiJournal a PST**
Para agregar MapiJournal a PST utilizando **Aspose.Email Java para PHP**, simplemente invoque el módulo **AddMapiJournalToPST**. Aquí puede ver un ejemplo de código.

**Código PHP**

``` php

 $d1 = new Date();

$calendar=new Calendar();

$cl = $calendar->getInstance();

$cl->setTime($d1);

$cl->add($calendar->HOUR, 1);

$d2 = $cl->getTime();

$journal = new MapiJournal("registro diario", "llamado en la oscuridad", "Llamada telefónica", "Llamada telefónica");

$journal->setStartTime($d1);

$journal->setEndTime($d2);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "JournalPST.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$journal_folder = $pst->createPredefinedFolder("Diario", $standardIpmFolder->Journal);

$journal_folder->addMapiMessageItem($journal);

print "Se agregó MapiJournal exitosamente.".PHP_EOL;

```
## **Descargar código en ejecución**
Descargue **Agregar MapiJournal a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)