---
title: Сохранить сообщение как черновик в Ruby
type: docs
weight: 70
url: /java/save-message-as-draft-in-ruby/
---

## **Aspose.Email - Сохранить сообщение как черновик**
Чтобы сохранить сообщение как черновик с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **SaveMessageAsDraft**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Создайте новый экземпляр класса MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Установите тему сообщения

message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Установите HTML-содержимое

message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

        "<font color=blue>Эта строка синего цвета</font>")

\# Установите информацию об отправителе

message.setFrom(mail_address.new("from@domain.com", "Имя отправителя", false))

\# Добавьте получателей в поле TO

message.getTo().add(mail_address.new("to1@domain.com", "Получатель 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Получатель 2", false))

\# Создайте экземпляр MapiMessage и загрузите в него экземпляр MailMessage

mapi_msg = Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(message)

\# Установите флаги MapiMessage как UNSENT и FROMME

mapi_message_flags = Rjb::import('com.aspose.email.MapiMessageFlags')

mapi_msg.setMessageFlags(mapi_message_flags.MSGFLAG_UNSENT || mapi_message_flags.MSGFLAG_FROMME)

\# Сохраните MapiMessage на диск

mapi_msg.save(data_dir + "New-Draft.msg")

\# Отобразите статус

puts "Черновик успешно сохранён."

```
## **Скачать рабочий код**
Скачайте **Сохранить сообщение как черновик (Aspose.Email)** с любого из нижеперечисленных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/savemessageasdraft.rb)