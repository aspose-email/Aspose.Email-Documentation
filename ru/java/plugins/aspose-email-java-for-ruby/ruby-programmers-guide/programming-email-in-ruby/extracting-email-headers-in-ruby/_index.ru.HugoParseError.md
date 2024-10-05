---
title: Извлечение заголовков электронной почты в Ruby
type: docs
weight: 50
url: /java/extracting-email-headers-in-ruby/
---

## **Aspose.Email - Извлечение заголовков электронной почты**
Чтобы извлечь заголовки электронной почты с помощью **Aspose.Email Java for Ruby**, просто вызовите модуль **ExtractEmailHeaders**. Здесь вы можете увидеть пример кода.

**Ruby Код**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Инициализация и загрузка существующего EML файла, указав формат сообщения

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "Вывод всех заголовков:"

\# Вывод всех заголовков

i=0

while i < message.getHeaders().getCount()

    puts message.getHeaders().get(i)

    i +=1

end 

```
## **Скачать работающий код**
Скачайте **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеупомянутых социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)