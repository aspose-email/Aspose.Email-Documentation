---
title: Working with Distribution Lists in Ruby
ArticleTitle: Working with Distribution Lists in Ruby
type: docs
weight: 50
url: /java/working-with-distribution-lists-in-ruby/
---

## **Aspose.Email - Working with Distribution Lists**
To Create Distribution List using **Aspose.Email Java for Ruby**, simply invoke **DistributionList** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

oneOffmembers = Rjb::import('com.aspose.email.MapiDistributionListMemberCollection').new

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("John R. Patrick", "JohnRPatrick@armyspy.com"))

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("Tilly Bates", "TillyBates@armyspy.com"))

dlist = Rjb::import('com.aspose.email.MapiDistributionList').new("Simple list", oneOffmembers)

dlist.setBody("Test body")

dlist.setSubject("Test subject")

dlist.setMileage("Test mileage")

dlist.setBilling("Test billing")

dlist.save(data_dir + "distlist.msg")

puts "Saved distribution list successfully."

```
## **Download Running Code**
Download **Working with Distribution Lists (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)
