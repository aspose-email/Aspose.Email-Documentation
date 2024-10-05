---
title: "Парсинг файлов сообщений Outlook на Ruby"
url: /ru/java/parsing-outlook-message-files-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Парсинг файлов сообщений Outlook**
Чтобы парсить файл сообщения Outlook с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **ParseOutlookMessageFile**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

outlook_message_file = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "Message.msg")

\# Показать имя отправителя

puts "Имя отправителя : " + outlook_message_file.getSenderName().to_s

# Показать тему

puts "Тема : " + outlook_message_file.getSubject().to_s

\# Показать тело

puts "Тело : " + outlook_message_file.getBody().to_s

```
## **Скачать работающий код**
Скачайте **Парсинг файлов сообщений Outlook (Aspose.Email)** с любого из упомянутых ниже социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)