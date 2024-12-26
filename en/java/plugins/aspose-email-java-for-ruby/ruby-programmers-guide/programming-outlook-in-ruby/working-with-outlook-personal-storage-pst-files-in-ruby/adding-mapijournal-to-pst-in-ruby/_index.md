---
title: Adding MapiJournal to PST in Ruby
ArticleTitle: Adding MapiJournal to PST in Ruby
type: docs
weight: 40
url: /java/adding-mapijournal-to-pst-in-ruby/
---

## **Aspose.Email - Adding MapiJournal to PST**
To Add MapiJournal to PST using **Aspose.Email Java for Ruby**, simply invoke **AddMapiJournalToPST** module. Here you can see example code.

**Ruby Code**

{{< highlight ruby >}}

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

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiJournal to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapijournaltopst.rb)
