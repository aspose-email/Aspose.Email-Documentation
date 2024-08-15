---
title: "Mostrar información de correo electrónico en la pantalla en PHP"
url: /es/java/displaying-email-information-on-screen-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Mostrar información de correo electrónico**
Para mostrar información de correo electrónico mediante **Aspose.Email Java para PHP**, simplemente invoca **GetEmailInfo** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

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
## **Descargar Running Code**
Download **Mostrar información de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/GetEmailInfo.php)
