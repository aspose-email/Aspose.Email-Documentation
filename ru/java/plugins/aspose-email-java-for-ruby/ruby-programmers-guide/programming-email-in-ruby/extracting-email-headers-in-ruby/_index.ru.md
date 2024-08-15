---
title: "Извлечение заголовков писем в Ruby"
url: /ru/java/extracting-email-headers-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Извлечение заголовков писем**
Извлечение заголовков электронных писем с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **ExtractEmailHeaders** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Initialize and Load an existing EML file by specifying the MessageFormat

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "Printing all Headers:"

\# Print out all the headers

i=0

while i < message.getHeaders().getCount()

    puts message.getHeaders().get(i)

    i +=1

end

```
## **Загрузить рабочий код**
Download **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)
