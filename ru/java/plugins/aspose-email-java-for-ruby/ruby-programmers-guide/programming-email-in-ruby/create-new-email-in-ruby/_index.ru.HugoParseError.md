---
title: Создание нового электронного письма в Ruby
type: docs
weight: 20
url: /java/create-new-email-in-ruby/
---

## **Aspose.Email - Создание нового электронного письма**
Чтобы создать новое электронное письмо с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **CreateNewEmail**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Создайте новый экземпляр класса MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Установите тему сообщения

message.setSubject("Новое сообщение, созданное с помощью Aspose.Email для Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Установите Html тело

message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

        "<font color=blue>Эта строка синего цвета</font>")

\# Установите информацию об отправителе

message.setFrom(mail_address.new("from@domain.com", "Имя отправителя", false))

\# Добавьте получателей TO

message.getTo().add(mail_address.new("to1@domain.com", "Получатель 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Получатель 2", false))

\# Добавьте получателей CC

message.getCC().add(mail_address.new("cc1@domain.com", "Получатель 3", false))

message.getCC().add(mail_address.new("cc2@domain.com", "Получатель 4", false))

\# Сохраните сообщение в форматах EML и MSG

mail_message_save_type = Rjb::import('com.aspose.email.MailMessageSaveType')

message.save(data_dir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(data_dir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Отобразите статус

puts "Сообщения электронной почты успешно созданы."

```
## **Скачать работающий код**
Скачайте **Создание нового электронного письма (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/createnewemail.rb)