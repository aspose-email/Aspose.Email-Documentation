---
title: "Adicionando MapiJournal ao PST em PHP"
url: /pt/java/adicionando-mapijournal-ao-pst-em-php/
weight: 40
type: docs
---

## **Aspose.Email - Adicionando MapiJournal ao PST**
Para adicionar MapiJournal ao PST usando **Aspose.Email Java para PHP**, basta invocar o módulo **AddMapiJournalToPST**. Aqui você pode ver um código de exemplo.

**Código PHP**

``` php

 $d1 = new Date();

$calendar=new Calendar();

$cl = $calendar->getInstance();

$cl->setTime($d1);

$cl->add($calendar->HOUR, 1);

$d2 = $cl->getTime();

$journal = new MapiJournal("registro diário", "chamado à meia-noite", "Chamada telefônica", "Chamada telefônica");

$journal->setStartTime($d1);

$journal->setEndTime($d2);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "JournalPST.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$journal_folder = $pst->createPredefinedFolder("Diário", $standardIpmFolder->Journal);

$journal_folder->addMapiMessageItem($journal);

print "MapiJournal adicionado com sucesso.".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiJournal ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST.php)