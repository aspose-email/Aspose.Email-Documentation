---
title: Отображение информации об электронной почте на экране в PHP
type: docs
weight: 30
url: /java/displaying-email-information-on-screen-in-php/
---

## **Aspose.Email - Отображение информации об электронной почте**

Чтобы отобразить информацию об электронной почте с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **GetEmailInfo**. Здесь вы можете видеть пример кода.

**PHP Код**

```php

 # Создание экземпляра MailMessage путем загрузки файла Eml

$message_format = new MessageFormat();

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "From: " . (string)$message->getFrom();

print "To: " . (string)$message->getTo();

print "Subject: " . (string)$message->getSubject();

print "HtmlBody: " . (string)$message->getHtmlBody();

print "TextBody: " . (string)$message->getTextBody();

```

## **Скачать рабочий код**

Скачайте **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеупомянутых социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)

