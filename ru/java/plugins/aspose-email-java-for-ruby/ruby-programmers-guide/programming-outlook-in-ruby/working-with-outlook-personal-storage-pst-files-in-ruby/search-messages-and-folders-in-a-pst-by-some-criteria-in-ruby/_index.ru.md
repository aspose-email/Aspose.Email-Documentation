---
title: "Поиск сообщений и папок в PST по некоторым критериям на Ruby"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Поиск сообщений и папок в PST**
Чтобы найти сообщения и папки в PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **SearchMessagesAndFoldersInPST**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Загрузите файл Outlook PST

pst = Rjb::import('com.aspose.email.PersonalStorage').fromFile(data_dir + "sample.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = Rjb::import('com.aspose.email.PersonalStorageQueryBuilder').new

\# Сообщения высокой важности

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

messages = folder.getContents(builder.getQuery())

puts "Сообщения с высокой важностью:" + messages.size().to_s

#builder = new PersonalStorageQueryBuilder();

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

puts "Сообщения с IPM.Note:" + messages.size().to_s

\# Сообщения с вложениями И высокой важностью

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Сообщения с вложениями: " + messages.size().to_s

\# Сообщения размером > 15 КБ

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

puts "сообщения размером > 15Кб:" + messages.size().to_s

\# Непрочитанные сообщения

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

puts "Непрочитанные:" + messages.size().to_s

\# Непрочитанные сообщения с вложениями

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Непрочитанные сообщения с вложениями: " + messages.size().to_s

```
## **Скачать рабочий код**
Скачайте **Поиск сообщений и папок в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/searchmessagesandfoldersinpst.rb)