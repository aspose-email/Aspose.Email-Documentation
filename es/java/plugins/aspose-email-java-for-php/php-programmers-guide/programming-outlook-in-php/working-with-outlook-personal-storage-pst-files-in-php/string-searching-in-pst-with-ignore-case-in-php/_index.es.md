---
title: "Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas en PHP"
url: /es/java/string-searching-in-pst-with-ignore-case-in-php/
weight: 80
type: docs
---

## **Aspose.Email: búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas**
Para buscar cadenas en PST con ignorar mayúsculas y minúsculas usando **Aspose.Email Java para PHP**, simplemente invoca **StringSearchInPST** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

```php

 $personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "search.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$fi = $pst->createPredefinedFolder("Inbox", $standardIpmFolder->Inbox);

$mapiMessage=new MapiMessage();

$mailMessage=new MailMessage();

$fi->addMessage($mapiMessage->fromMailMessage($mailMessage->load($dataDir . "search.pst")));

$builder = new MailQueryBuilder();

$builder->getFrom()->contains("automated", true);

$query = $builder->getQuery();

$coll = $fi->getContents($query);

print "Total Results:" . (string)$coll->size();

```
## **Descargar Running Code**
Download **Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
