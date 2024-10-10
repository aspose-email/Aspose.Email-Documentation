---
title: "Сохранить сообщение как черновик в PHP"
url: /ru/java/save-message-as-draft-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Сохранить сообщение как черновик**
Чтобы сохранить сообщение как черновик с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **SaveMessageAsDraft**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 # Создать новый экземпляр класса MailMessage

$message = new MailMessage();

\# Установить тему сообщения

$message->setSubject("Новое сообщение, созданное Aspose.Email для Java");

$mail_address = new MailAddress();

\# Установить Html тело

$message->setHtmlBody("<b>Эта строка жирная.</b> <br/> <br/>" .

"<font color=blue>Эта строка синего цвета</font>");

\# Установить информацию об отправителе

$message->setFrom(new MailAddress("from@domain.com", "Имя отправителя", false));

\# Добавить получателей в поле TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Получатель 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Получатель 2", false));

\# Создать экземпляр MapiMessage и загрузить экземпляр MailMessag в него

$mapiMessage=new MapiMessage();

$mapi_msg = $mapiMessage->fromMailMessage($message);

\# Установить флаги MapiMessageFlags как UNSENT и FROMME

$mapi_message_flags = new MapiMessageFlags();

\# Сохранить MapiMessage на диск

$mapi_msg->save($dataDir . "New-Draft.msg");

\# Показать статус

print "Черновик успешно сохранён.".PHP_EOL;

```
## **Скачать рабочий код**
Скачайте **Сохранить сообщение как черновик (Aspose.Email)** с любого из указанных ниже социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)