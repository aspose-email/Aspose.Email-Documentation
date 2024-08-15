---
title: "Поиск строк в PST с игнорированием регистра в PHP"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-php/
weight: 80
type: docs
---

## **Aspose.Email - поиск строк в PST с регистром игнорирования**
Для поиска строк в PST с помощью Ignore Case используйте **Aspose.Электронная почта Java для PHP**, просто вызовите **StringSearchInPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Поиск строк в PST с использованием регистра игнорирования (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
