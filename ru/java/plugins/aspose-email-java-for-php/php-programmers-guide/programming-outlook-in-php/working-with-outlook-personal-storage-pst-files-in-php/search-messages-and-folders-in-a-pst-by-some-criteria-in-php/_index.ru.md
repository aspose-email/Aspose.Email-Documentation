---
title: "Поиск сообщений и папок в PST по некоторым критериям на PHP"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Поиск сообщений и папок в PST**
Чтобы выполнить поиск сообщений и папок в PST с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **SearchMessagesAndFoldersInPST**. Здесь вы можете увидеть пример кода.

**PHP код**

```php

 # Загрузить файл Outlook PST

$personalStorage=new PersonalStorage();

$pst = $personalStorage->fromFile($dataDir . "sample1.pst");

$folder = $pst->getRootFolder()->getSubFolder("myInbox");

$builder = new PersonalStorageQueryBuilder();

\# Сообщения высокой важности

$mapiImportance=new MapiImportance();

$builder->getImportance()->equals($mapiImportance->High);

$messages = $folder->getContents($builder->getQuery());

print "Сообщения с высокой важностью:" . (string)$messages->size();

#builder = new PersonalStorageQueryBuilder();

$builder->getMessageClass()->equals("IPM.Note");

$messages = $folder->getContents($builder->getQuery());

print "Сообщения с IPM.Note:" . (string)$messages->size();

\# Сообщения с вложениями И высокой важностью

$builder->getImportance()->equals($mapiImportance->High);

$mapiMessageFlags=new MapiMessageFlags();

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Сообщения с вложениями: " . (string)$messages->size();

\# Сообщения размером больше 15 КБ

$builder->getMessageSize()->greater(15000);

$messages = $folder->getContents($builder->getQuery());

print "сообщения размером > 15 Кб:" . (string)$messages->size();

\# Непрочитанные сообщения

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$messages = $folder->getContents($builder->getQuery());

print "Непрочитанные:" . (string)$messages->size();//.to_s

\# Непрочитанные сообщения с вложениями

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Непрочитанные сообщения с вложениями: " . (string)$messages->size();

```
## **Скачать рабочий код**
Скачайте **Поиск сообщений и папок в PST (Aspose.Email)** с любого из упомянутых ниже сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)