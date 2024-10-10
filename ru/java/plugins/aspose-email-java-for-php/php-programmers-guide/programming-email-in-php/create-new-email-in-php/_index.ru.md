---
title: "Создание нового электронного письма в PHP"
url: /ru/java/create-new-email-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Создание нового электронного письма**
Для создания нового электронного письма с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **CreateNewEmail**. Здесь вы можете увидеть пример кода.

**PHP код**

``` php

 # Создать новый экземпляр класса MailMessage

$message = new MailMessage();

\# Установить тему сообщения

$message->setSubject("Новое сообщение, созданное Aspose.Email для Java");

$mail_address = new MailAddress();

\# Установить HTML содержимое

$message->setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" .

"<font color=blue>Эта строка синего цвета</font>");

\# Установить информацию отправителя

$message->setFrom(new MailAddress("from@domain.com", "Имя отправителя", false));

\# Добавить получателей в поле TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Получатель 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Получатель 2", false));

\# Добавить получателей в поле CC

$message->getCC()->add(new MailAddress("cc1@domain.com", "Получатель 3", false));

$message->getCC()->add(new MailAddress("cc2@domain.com", "Получатель 4", false));

\# Сохранить сообщение в форматах EML и MSG

$mail_message_save_type = new MailMessageSaveType();

$message->save($dataDir . "Message.eml", $mail_message_save_type->getEmlFormat());

$message->save($dataDir . "Message.msg", $mail_message_save_type->getOutlookMessageFormat());

\# Отобразить статус

print "Электронные письма успешно созданы.".PHP_EOL;


```
## **Скачать рабочий код**
Скачать **Создание нового электронного письма (Aspose.Email)** с любых из ниже перечисленных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/CreateNewEmail.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/CreateNewEmail.php)