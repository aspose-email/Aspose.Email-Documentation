---
title: Обновление и сохранение электронной почты в PHP
type: docs
weight: 70
url: /java/update-and-save-an-email-in-php/
---

## **Aspose.Email - Обновление и сохранение электронной почты**
Чтобы обновить и сохранить электронное письмо с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **UpdateEmail**. Здесь вы можете увидеть пример кода.

**PHP код**

``` php

 # Инициализировать и загрузить существующий MSG файл, указав формат сообщения

$mailMessage=new MailMessage();

$email = $mailMessage->load($dataDir . "Message.msg");

\# Инициализировать строковую переменную для получения темы письма

$subject = $email->getSubject();

\# Установить тему письма

$email->setSubject('Этот текст добавлен к существующей теме');

\# Инициализировать строковую переменную для получения HTML-содержимого письма

$body = $email->getHtmlBody();

\# Добавить еще немного информации к переменной Body

$body = $body . "<br> Этот текст добавлен к существующему содержимому".PHP_EOL;

\# Установить содержимое письма

$email->setHtmlBody($body);

\# Инициализировать объект MailAddressCollection

$contacts = new MailAddressCollection();

\# Получить список адресатов электронного письма

$contacts = $email->getTo();

\# Добавить другой адрес электронной почты в коллекцию

$contacts->add("to1@domain.com");

\# Установить коллекцию как список адресатов электронного письма

$email->setTo($contacts);

\# Инициализировать MailAddressCollection

$contacts = new MailAddressCollection();

\# Получить список CC электронного письма

$contacts = $email->getCC();

\# Добавить другой адрес электронной почты в коллекцию

$contacts->add("cc2@domain.com");

\# Установить коллекцию как список CC электронного письма

$email->setCC($contacts);

\# Сохранить сообщение электронной почты на диск, указав формат сообщения

$mailMessageSaveType=new MailMessageSaveType();

$email->save($dataDir . "UpdateMessage.msg", $mailMessageSaveType->getOutlookMessageFormat());

\# Отобразить статус

print "Сообщение электронной почты успешно обновлено.".PHP_EOL;

```
## **Скачать работающий код**
Скачать **Обновление и сохранение электронной почты (Aspose.Email)** с любого из нижеупомянутых сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/UpdateEmail.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/UpdateEmail.php)