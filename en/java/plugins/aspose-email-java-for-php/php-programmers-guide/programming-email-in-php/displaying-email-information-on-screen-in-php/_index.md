---
title: Displaying Email Information on Screen in PHP
ArticleTitle: Displaying Email Information on Screen in PHP
type: docs
weight: 30
url: /java/displaying-email-information-on-screen-in-php/
---

## **Aspose.Email - Displaying Email Information**
To Display Email Information using **Aspose.Email Java for PHP**, simply invoke **GetEmailInfo** module. Here you can see example code.

**PHP Code**

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
## **Download Running Code**
Download **Displaying Email Information (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
