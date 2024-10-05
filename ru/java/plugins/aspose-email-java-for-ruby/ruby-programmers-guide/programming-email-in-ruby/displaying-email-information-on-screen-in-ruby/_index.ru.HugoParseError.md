---
title: Отображение информации об электронной почте на экране в Ruby
type: docs
weight: 40
url: /java/displaying-email-information-on-screen-in-ruby/
---

## **Aspose.Email - Отображение информации об электронной почте**
Чтобы отобразить информацию об электронной почте с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **GetEmailInfo**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Создайте экземпляр MailMessage, загрузив файл Eml

message_format = Rjb::import('com.aspose.email.MessageFormat')

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "От: " + message.getFrom().to_string

puts "Кому: " + message.getTo().to_string

puts "Тема: " + message.getSubject().to_s

puts "HtmlBody: " + message.getHtmlBody().to_s

puts "TextBody: " + message.getTextBody().to_s

```
## **Скачать работающий код**
Скачайте **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеупомянутых сайтов по социальному кодированию:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)