---
title: Adding Files to PST in Ruby
type: docs
weight: 10
url: /java/adding-files-to-pst-in-ruby/
---

## **Aspose.Email - Adding Files to PST**
To Add File to PST using **Aspose.Email Java for Ruby**, simply invoke **AddFileToPST** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "AddFile.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addFile(data_dir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

pst.dispose()

puts "Added file to PST"

```
## **Download Running Code**
Download **Adding Files to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addfiletopst.rb)
