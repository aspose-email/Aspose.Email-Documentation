---
title: "Конвертация электронных сообщений в Ruby"
url: /ru/java/converting-email-messages-in-ruby/
weight: 10
type: docs
---

## **Aspose.Email - Конвертация электронных сообщений**
Чтобы конвертировать электронные письма с использованием **Aspose.Email Java для Ruby**, вызовите метод **convert_eml_to_msg** из модуля **Converter**. Здесь вы можете увидеть пример кода.

**Ruby код**

``` ruby

 def convert_eml_to_msg()    

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Инициализировать и загрузить существующий EML файл, указав формат сообщения

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Сохранить электронное сообщение на диск в формате Unicode

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Показать статус

    puts "Успешно конвертировано eml в msg."

end

```
## **Скачать рабочий код**
Скачайте **Конвертацию электронных сообщений (Aspose.Email)** с любого из нижеупомянутых сайтов для социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)