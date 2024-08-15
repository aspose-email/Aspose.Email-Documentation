---
title: "Отображение информации об электронной почте на экране в PHP"
url: /ru/java/displaying-email-information-on-screen-in-php/
weight: 30
type: docs
---

## **Aspose.Email - отображение информации об электронной почте**
Для отображения информации об электронной почте с помощью **Aspose.Электронная почта Java для PHP**, просто вызовите **GetEmailInfo** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

``` php

 # Create MailMessage instance by loading an Eml file

$message_format = new MessageFormat();

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "From: " . (string)$message->getFrom();

print "To: " . (string)$message->getTo();

print "Subject: " . (string)$message->getSubject();

print "HtmlBody: " . (string)$message->getHtmlBody();

print "TextBody: " . (string)$message->getTextBody();

```
## **Загрузить рабочий код**
Download **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
