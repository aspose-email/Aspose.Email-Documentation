---
title: "Agregar MapiJournal a PST en Ruby"
url: /es/java/adding-mapijournal-to-pst-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Agregar MapiJournal a PST**
Para agregar MapiJournal a PST usando **Aspose.Email Java para Ruby**, simplemente invoca **AddMapiJournalToPST** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Agregar MapiJournal a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapijournaltopst.rb)
