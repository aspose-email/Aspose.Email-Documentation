---
title: Извлечение заголовков электронной почты в PHP
type: docs
weight: 40
url: /java/extracting-email-headers-in-php/
---

## **Aspose.Email - Извлечение заголовков электронной почты**
Чтобы извлечь заголовки электронной почты с помощью **Aspose.Email Java for PHP**, просто вызовите модуль **ExtractEmailHeaders**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 # Инициализируйте и загрузите существующий EML файл, указав формат сообщения

$mailMessage=new MailMessage();

$message = $mailMessage->load($dataDir . "Message.eml");

print "Печатаем все заголовки:".PHP_EOL;

\# Выведите все заголовки

$i=0;

while ($i < sizeof($message->getHeaders()->getCount())) {

print $message.$message->getHeaders()->get($i);

$i += 1;

}

```
## **Скачать работающий код**
Скачайте **Извлечение заголовков электронной почты (Aspose.Email)** с любого из указанных ниже сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/ExtractEmailHeaders.php)