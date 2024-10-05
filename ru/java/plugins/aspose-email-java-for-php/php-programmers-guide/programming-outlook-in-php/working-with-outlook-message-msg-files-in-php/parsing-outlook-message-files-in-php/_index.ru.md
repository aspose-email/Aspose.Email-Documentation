---
title: "Парсинг файлов сообщений Outlook на PHP"
url: /ru/java/parsing-outlook-message-files-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Парсинг файлов сообщений Outlook**
Чтобы парсить файл сообщений Outlook с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **ParseOutlookMessageFile**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Отобразить имя отправителя

print "Имя отправителя : " . $outlook_message_file->getSenderName();

#Отобразить тему

print "Тема : " . $outlook_message_file->getSubject();

\# Отобразить тело

print "Тело : " . $outlook_message_file->getBody();

```
## **Скачать работающий код**
Скачайте **Парсинг файлов сообщений Outlook (Aspose.Email)** с любого из нижеупомянутых сайтов социального кода:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)