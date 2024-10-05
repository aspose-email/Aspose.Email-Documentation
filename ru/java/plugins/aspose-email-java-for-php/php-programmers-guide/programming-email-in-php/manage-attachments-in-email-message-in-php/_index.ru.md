---
title: "Управление вложениями в электронных сообщениях на PHP"
url: /ru/java/manage-attachments-in-email-message-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Управление вложениями в электронных сообщениях**
Чтобы добавить вложения к новому электронному сообщению, используя **Aspose.Email Java для PHP**, вызовите метод **add_attachments** модуля **ManageAttachments**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 public static function add_attachments($dataDir=null){

\# Создание нового экземпляра класса MailMessage

$message =new MailMessage();

\# Установка темы сообщения

$message->setSubject("Новое сообщение создано с помощью Aspose.Email для Java");

$mail_address = new MailAddress();

\# Установка Html содержимого

$message->setHtmlBody("<b>Эта строка выделена жирным.</b> <br/> <br/>" .

"<font color=blue>Эта строка синего цвета</font>");

\# Установка информации об отправителе

$message->setFrom(new MailAddress("from@domain.com", "Имя отправителя", false));

\# Добавление получателей в поле TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Получатель 1", false));

\# Добавление вложения

\# Загрузка вложения

$attachment = new Attachment($dataDir . "1.txt");

\# Добавление вложения в экземпляр класса MailMessage

$message->addAttachment($attachment);

\# Сохранение сообщения на диск

$messageFormat=new MessageFormat();

$message->save($dataDir . "Add-Attachment.msg", $messageFormat->getMsg());

\# Отображение статуса

print "Вложение успешно добавлено.".PHP_EOL;

}

```
## **Скачать работающий код**
Скачайте **Управление вложениями в электронных сообщениях (Aspose.Email)** с любого из упомянутых ниже сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ManageAttachments.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/ManageAttachments.php)