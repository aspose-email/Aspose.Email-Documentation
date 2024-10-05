---
title: Конвертация Email Сообщений в PHP
type: docs
weight: 10
url: /java/converting-email-messages-in-php/
---

## **Aspose.Email - Конвертация Email Сообщений**

Для конвертации Email сообщений с помощью **Aspose.Email Java for PHP**, вызовите метод **convert_eml_to_msg** модуля **Converter**. Здесь вы можете увидеть пример кода.

**PHP Код**

```php
 public static function convert_eml_to_msg($dataDir=null){

\# Инициализация и загрузка существующего EML файла, указав формат сообщения

$mailMessage=new MailMessage();

$eml = $mailMessage->load($dataDir . "Message.eml");

\# Сохранение Email сообщения на диск в формате Unicode

$saveOptions=new SaveOptions();

$eml->save($dataDir . "AnEmail.msg", $saveOptions->getDefaultMsgUnicode());

\# Отображение Статуса

print "Email успешно конвертирован в msg.".PHP_EOL;

}
```

## **Скачать Рабочий Код**

Скачайте **Конвертацию Email Сообщений (Aspose.Email)** с любого из перечисленных ниже социальных сайтов кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/Converter.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/Converter.php)

