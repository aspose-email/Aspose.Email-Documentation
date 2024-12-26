---
title: String Searching in PST with Ignore Case in Ruby
ArticleTitle: String Searching in PST with Ignore Case in Ruby
type: docs
weight: 90
url: /java/string-searching-in-pst-with-ignore-case-in-ruby/
---

## **Aspose.Email - String Searching in PST with Ignore Case**
To string Searching in PST with Ignore Case using **Aspose.Email Java for Ruby**, simply invoke **StringSearchInPST** module. Here you can see example code.

**Ruby Code**

{{< highlight ruby >}}

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

{{< /highlight >}}
## **Download Running Code**
Download **String Searching in PST with Ignore Case (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)
