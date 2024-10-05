---
title: Создание нового PST в Ruby
type: docs
weight: 70
url: /java/create-new-pst-in-ruby/
---

## **Aspose.Email - Создание нового PST**

Чтобы создать новый PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **CreatePST**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Создайте экземпляр PersonalStorage

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "sample1.pst", 0)

\# Создайте папку в корне pst

pst.getRootFolder().addSubFolder("myInbox")

\# Добавьте сообщение в новосозданную папку

mapi_message = Rjb::import('com.aspose.email.MapiMessage')

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(data_dir + "Message.msg"))

puts "PST успешно создан."

```

## **Скачать работающий код**

Скачайте **Создание нового PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)

