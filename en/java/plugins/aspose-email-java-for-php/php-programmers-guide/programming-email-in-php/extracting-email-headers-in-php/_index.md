---
title: Extracting Email Headers in PHP
ArticleTitle: Extracting Email Headers in PHP
type: docs
weight: 40
url: /java/extracting-email-headers-in-php/
---

## **Aspose.Email - Extracting Email Headers**
To Extract Email Headers using **Aspose.Email Java for PHP**, simply invoke **ExtractEmailHeaders** module. Here you can see example code.

**PHP Code**

``` php

 # Initialize and Load an existing EML file by specifying the MessageFormat

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "Printing all Headers:".PHP_EOL;

\# Print out all the headers

$i=0;

while ($i < sizeof($message->getHeaders()->getCount())) {

print $message.$message->getHeaders()->get($i);

$i += 1;

}

```
## **Download Running Code**
Download **Extracting Email Headers (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
