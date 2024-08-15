---
title: "Преобразование сообщений электронной почты в Ruby"
url: /ru/java/converting-email-messages-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - конвертация сообщений электронной почты**
Для преобразования сообщений электронной почты с помощью **Aspose.Электронная почта Java для Ruby**, позвоните **convert_eml_to_msg** метод **Converter** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 def convert_eml_to_msg()   

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Initialize and Load an existing EML file by specifying the MessageFormat

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Save the Email message to disk in Unicode format

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Display Status

    puts "Converted eml to msg successfully."

end

```
## **Загрузить рабочий код**
Download **Преобразование сообщений электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)
