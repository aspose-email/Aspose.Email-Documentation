---
title: "Поиск строк в PST с учетом регистра в PHP"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-php/
weight: 80
type: docs
---

## **Aspose.Email - Поиск строк в PST с учетом регистра**
Для поиска строк в PST с учетом регистра, используя **Aspose.Email Java для PHP**, просто вызовите модуль **StringSearchInPST**. Здесь вы можете увидеть пример кода.

**PHP код**

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

print "Всего результатов:" . (string)$coll->size();

```
## **Скачать работающий код**
Скачайте **Поиск строк в PST с учетом регистра (Aspose.Email)** с любого из нижеупомянутых социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST.php)