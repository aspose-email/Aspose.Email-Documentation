---
title: "Настройка Заголовков Писем в Ruby"
url: /ru/java/customizing-email-headers-in-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Настройка Заголовков Писем**
Чтобы настроить заголовки писем с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **CustomizeEmailHeaders**. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Создайте новый экземпляр класса MailMessage

message = Rjb::import('com.aspose.email.MailMessage').new

\# Установите тему сообщения

message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

\# Установите Html тело

message.setHtmlBody("<b>Эта строка выделена жирным.</b> <br/> <br/>" +

        "<font color=blue>Эта строка синего цвета</font>")

\# Установите информацию отправителя

message.setFrom(Rjb::import('com.aspose.email.MailAddress').new("from@domain.com", "Имя Отправителя", false))

\# Добавьте получателей TO

message.getTo().add(Rjb::import('com.aspose.email.MailAddress').new("to@domain.com", "Получатель 1", false))

\# Тема сообщения

message.setSubject("Настройка Заголовков Писем")

\# Укажите дату

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Укажите XMailer

message.setXMailer("Aspose.Email")

\# Укажите Секретный Заголовок

message.getHeaders().add("secret-header", "mystery")

\# Сохраните сообщение на диск

message.save(data_dir + "MsgHeaders.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

\# Выведите Статус

puts "Заголовки сообщения успешно настроены."

```
## **Скачать Рабочий Код**
Скачайте **Настройка Заголовков Писем (Aspose.Email)** с любого из нижеуказанных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/customizeemailheaders.rb)