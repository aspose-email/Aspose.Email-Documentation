---
title: "Извлечение заголовков электронной почты в PHP"
url: /ru/java/extracting-email-headers-in-php/
weight: 40
type: docs
---

## **Aspose.Email - Извлечение заголовков писем**
Извлечение заголовков электронных писем с помощью **Aspose.Электронная почта Java для PHP**, просто вызовите **ExtractEmailHeaders** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
