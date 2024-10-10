---
title: "Поиск строк в PST с игнорированием регистра в Ruby"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-ruby/
weight: 90
type: docs
---

## **Aspose.Email - Поиск строк в PST с игнорированием регистра**
Для поиска строк в PST с игнорированием регистра, используя **Aspose.Email Java для Ruby**, просто вызовите модуль **StringSearchInPST**. Здесь вы можете увидеть пример кода.

**Код Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Загрузите файл PST Outlook

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "search.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Входящие", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addMessage(Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(Rjb::import('com.aspose.email.MailMessage').load(data_dir + "search.pst")))

builder = Rjb::import('com.aspose.email.MailQueryBuilder').new

builder.getFrom().contains("автоматизированный", true)

query = builder.getQuery()

coll = fi.getContents(query)

puts "Всего результатов:" + coll.size().to_s

```
## **Скачать рабочий код**
Скачайте **Поиск строк в PST с игнорированием регистра (Aspose.Email)** с любого из ниже перечисленных сайтов для совместной разработки:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)