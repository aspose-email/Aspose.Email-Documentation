---
title: "Поиск сообщений и папок в PST по некоторым критериям в PHP"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-php/
weight: 70
type: docs
---

## **Aspose.Email - поиск сообщений и папок в PST**
Для поиска сообщений и папок в PST с помощью **Aspose.Электронная почта Java для PHP**, просто вызовите **SearchMessagesAndFoldersInPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

```php

 # Load the Outlook PST file

$personalStorage=new PersonalStorage();

$pst = $personalStorage->fromFile($dataDir . "sample1.pst");

$folder = $pst->getRootFolder()->getSubFolder("myInbox");

$builder = new PersonalStorageQueryBuilder();

\# High importance messages

$mapiImportance=new MapiImportance();

$builder->getImportance()->equals($mapiImportance->High);

$messages = $folder->getContents($builder->getQuery());

print "Messages with High Imp:" . (string)$messages->size();

#builder = new PersonalStorageQueryBuilder();

$builder->getMessageClass()->equals("IPM.Note");

$messages = $folder->getContents($builder->getQuery());

print "Messages with IPM.Note:" . (string)$messages->size();

\# Messages with attachments AND high importance

$builder->getImportance()->equals($mapiImportance->High);

$mapiMessageFlags=new MapiMessageFlags();

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Messages with atts: " . (string)$messages->size();

\# Messages with size > 15 KB

$builder->getMessageSize()->greater(15000);

$messages = $folder->getContents($builder->getQuery());

print "messags size > 15Kb:" . (string)$messages->size();

\# Unread messages

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$messages = $folder->getContents($builder->getQuery());

print "Unread:" . (string)$messages->size();//.to_s

\# Unread messages with attachments

$builder->hasNoFlags($mapiMessageFlags->MSGFLAG_READ);

$builder->hasFlags($mapiMessageFlags->MSGFLAG_HASATTACH);

$messages = $folder->getContents($builder->getQuery());

print "Unread msgs with atts: " . (string)$messages->size();

```
## **Загрузить рабочий код**
Download **Поиск сообщений и папок в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST.php)
