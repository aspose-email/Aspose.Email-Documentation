---
title: "Búsqueda de Cadenas en PST con Ignorar Mayúsculas en PHP"
url: /es/java/string-searching-in-pst-with-ignore-case-in-php/
weight: 80
type: docs
---

## **Aspose.Email - Búsqueda de Cadenas en PST con Ignorar Mayúsculas**
Para buscar cadenas en PST con ignorar mayúsculas usando **Aspose.Email Java para PHP**, simplemente invoca el módulo **StringSearchInPST**. Aquí puedes ver un ejemplo de código.

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
## **Descargar Código en Ejecución**
Descarga **Búsqueda de Cadenas en PST con Ignorar Mayúsculas (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)