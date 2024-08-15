---
title: "Работа со списками рассылки в Ruby"
url: /ru/java/working-with-distribution-lists-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Работа со списками рассылки**
Для создания списка рассылки с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **DistributionList** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

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
## **Загрузить рабочий код**
Download **Работа со списками рассылки (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)
