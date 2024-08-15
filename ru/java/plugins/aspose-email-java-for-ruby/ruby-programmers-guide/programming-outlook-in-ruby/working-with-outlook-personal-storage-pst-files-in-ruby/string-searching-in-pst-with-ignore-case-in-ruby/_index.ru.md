---
title: "Поиск строк в PST с игнорированием регистра в Ruby"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-ruby/
weight: 90
type: docs
---

## **Aspose.Email - поиск строк в PST с регистром игнорирования**
Для поиска строк в PST с помощью Ignore Case используйте **Aspose.Электронная почта Java для Ruby**, просто вызовите **StringSearchInPST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Load the Outlook PST file

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "search.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addMessage(Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(Rjb::import('com.aspose.email.MailMessage').load(data_dir + "search.pst")))

builder = Rjb::import('com.aspose.email.MailQueryBuilder').new

builder.getFrom().contains("automated", true)

query = builder.getQuery()

coll = fi.getContents(query)

puts "Total Results:" + coll.size().to_s

```
## **Загрузить рабочий код**
Download **Поиск строк в PST с использованием регистра игнорирования (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)
