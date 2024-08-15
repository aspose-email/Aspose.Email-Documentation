---
title: "Добавление журнала MapiJournal в PST в Ruby"
url: /ru/java/adding-mapijournal-to-pst-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Добавление журнала MapiJournal в PST**
Чтобы добавить MapiJournal в PST, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **AddMapiJournalToPST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

d1 = Rjb::import('java.util.Date').new

cl = Rjb::import('java.util.Calendar').getInstance()

cl.setTime(d1)

cl.add(Rjb::import('java.util.Calendar').HOUR, 1)

d2 = cl.getTime()

journal = Rjb::import('com.aspose.email.MapiJournal').new("daily record", "called out in the dark", "Phone call", "Phone call")

journal.setStartTime(d1)

journal.setEndTime(d2)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "JournalPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

journal_folder = pst.createPredefinedFolder("Journal", Rjb::import('com.aspose.email.StandardIpmFolder').Journal)

journal_folder.addMapiMessageItem(journal)

puts "Added MapiJournal Successfully."

```
## **Загрузить рабочий код**
Download **Добавление журнала MAPIjournal в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapijournaltopst.rb)
