---
title: Converting Email Messages in PHP
type: docs
weight: 10
url: /java/converting-email-messages-in-php/
---

## **Aspose.Email - Converting Email Messages**
To Convert Email Messages using **Aspose.Email Java for PHP**, call **convert_eml_to_msg** method of **Converter** module. Here you can see example code.

**PHP Code**

``` php

 public static function convert_eml_to_msg($dataDir=null){

\# Initialize and Load an existing EML file by specifying the MessageFormat

$mailMessage=new MailMessage();

$eml = $mailMessage->load($dataDir . "Message.eml");

\# Save the Email message to disk in Unicode format

$saveOptions=new SaveOptions();

$eml->save($dataDir . "AnEmail.msg", $saveOptions->getDefaultMsgUnicode());

\# Display Status

print "Converted email to msg successfully.".PHP_EOL;

}

```
## **Download Running Code**
Download **Converting Email Messages (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)
