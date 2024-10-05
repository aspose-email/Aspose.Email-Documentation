---
title: "Обновление и сохранение электронной почты в Ruby"
url: /ru/java/update-and-save-an-email-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Обновление и сохранение электронной почты**
Для обновления и сохранения электронной почты с использованием **Aspose.Email Java для Ruby** просто вызовите модуль **UpdateEmail**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Инициализация и загрузка существующего MSG файла, указывая формат сообщения

email = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.msg")

\# Инициализация строковой переменной для получения темы электронной почты

subject = email.getSubject()

\# Добавление дополнительной информации к теме

subject = subject + " Этот текст добавлен к существующей теме"

\# Установка темы электронной почты

email.setSubject(subject)

\# Инициализация строковой переменной для получения HTML-содержимого электронной почты

body = email.getHtmlBody()

\# Добавление дополнительной информации к переменной Body

body = body + "<br> Этот текст добавлен к существующему содержимому"

\# Установка содержимого электронной почты

email.setHtmlBody(body)

\# Инициализация объекта MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Получение списка получателей электронного письма

contacts = email.getTo()

\# Добавление еще одного адреса электронной почты в коллекцию

contacts.add("to1@domain.com")

\# Установка коллекции как списка получателей электронной почты

email.setTo(contacts)

\# Инициализация MailAddressCollection

contacts = Rjb::import('com.aspose.email.MailAddressCollection').new

\# Получение списка CC электронной почты

contacts = email.getCC()

\# Добавление еще одного адреса электронной почты в коллекцию

contacts.add("cc2@domain.com")

\# Установка коллекции как списка CC электронной почты

email.setCC(contacts)

\# Сохранение сообщения электронной почты на диск, указывая формат сообщения

email.save(data_dir + "UpdateMessage.msg", Rjb::import('com.aspose.email.MailMessageSaveType').getOutlookMessageFormat())

\# Отображение статуса

puts "Сообщение электронной почты успешно обновлено."

```
## **Скачать работающий код**
Скачайте **Обновление и сохранение электронной почты (Aspose.Email)** с любого из нижеупомянутых сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/updateemail.rb)