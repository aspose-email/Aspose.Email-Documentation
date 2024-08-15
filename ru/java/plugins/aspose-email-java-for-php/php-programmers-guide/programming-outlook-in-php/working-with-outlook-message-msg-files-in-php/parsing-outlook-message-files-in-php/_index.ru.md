---
title: "Разбор файлов сообщений Outlook в PHP"
url: /ru/java/parsing-outlook-message-files-in-php/
weight: 30
type: docs
---

## **Aspose.Email - парсинг файлов сообщений Outlook**
Для анализа файла сообщений Outlook с помощью **Aspose.Электронная почта Java для PHP**, просто вызовите **ParseOutlookMessageFile** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

``` php

 $mapiMessage=new MapiMessage();

$outlook_message_file = $mapiMessage->fromFile($dataDir . "Message.msg");

\# Display sender's name

print "Sender Name : " . $outlook_message_file->getSenderName();

#Display Subject

print "Subject : " . $outlook_message_file->getSubject();

\# Display Body

print "Body : " . $outlook_message_file->getBody();

```
## **Загрузить рабочий код**
Download **Разбор файлов сообщений Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile.php)
