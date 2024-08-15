---
title: "Отображение информации об электронной почте на экране в Ruby"
url: /ru/java/displaying-email-information-on-screen-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - отображение информации об электронной почте**
Для отображения информации об электронной почте с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **GetEmailInfo** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Create MailMessage instance by loading an Eml file

message_format = Rjb::import('com.aspose.email.MessageFormat')

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "From: " + message.getFrom().to_string

puts "To: " + message.getTo().to_string

puts "Subject: " + message.getSubject().to_s

puts "HtmlBody: " + message.getHtmlBody().to_s

puts "TextBody: " + message.getTextBody().to_s

```
## **Загрузить рабочий код**
Download **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)
