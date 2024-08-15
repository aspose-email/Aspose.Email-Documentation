---
title: "Разбор файлов сообщений Outlook в Ruby"
url: /ru/java/parsing-outlook-message-files-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - парсинг файлов сообщений Outlook**
Для анализа файла сообщений Outlook с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **ParseOutlookMessageFile** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

outlook_message_file = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "Message.msg")

\# Display sender's name

puts "Sender Name : " + outlook_message_file.getSenderName().to_s

#Display Subject

puts "Subject : " + outlook_message_file.getSubject().to_s

\# Display Body

puts "Body : " + outlook_message_file.getBody().to_s

```
## **Загрузить рабочий код**
Download **Разбор файлов сообщений Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)
