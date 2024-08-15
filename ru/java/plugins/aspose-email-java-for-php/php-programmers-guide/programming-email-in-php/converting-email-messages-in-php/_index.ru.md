---
title: "Преобразование сообщений электронной почты в PHP"
url: /ru/java/converting-email-messages-in-php/
weight: 10
type: docs
---

## **Aspose.Email - конвертация сообщений электронной почты**
Для преобразования сообщений электронной почты с помощью **Aspose.Электронная почта Java для PHP**, позвоните **convert_eml_to_msg** метод **Converter** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Преобразование сообщений электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)
