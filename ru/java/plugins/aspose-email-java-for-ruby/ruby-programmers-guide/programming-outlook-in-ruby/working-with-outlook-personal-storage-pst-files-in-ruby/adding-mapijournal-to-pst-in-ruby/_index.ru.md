---
title: "Добавление MapiJournal в PST на Ruby"
url: /ru/java/adding-mapijournal-to-pst-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Добавление MapiJournal в PST**
Чтобы добавить MapiJournal в PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **AddMapiJournalToPST**. Здесь вы можете увидеть пример кода.

**Ruby Код**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

d1 = Rjb::import('java.util.Date').new

cl = Rjb::import('java.util.Calendar').getInstance()

cl.setTime(d1)

cl.add(Rjb::import('java.util.Calendar').HOUR, 1)

d2 = cl.getTime()

journal = Rjb::import('com.aspose.email.MapiJournal').new("ежедневная запись", "позвонил в темноте", "Телефонный звонок", "Телефонный звонок")

journal.setStartTime(d1)

journal.setEndTime(d2)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "JournalPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

journal_folder = pst.createPredefinedFolder("Журнал", Rjb::import('com.aspose.email.StandardIpmFolder').Journal)

journal_folder.addMapiMessageItem(journal)

puts "MapiJournal успешно добавлен."

```
## **Скачать рабочий код**
Скачайте **Добавление MapiJournal в PST (Aspose.Email)** с любого из нижеупомянутых социальных кодинговых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapijournaltopst.rb)