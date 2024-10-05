---
title: Работа с рассылками в Ruby
type: docs
weight: 50
url: /java/working-with-distribution-lists-in-ruby/
---

## **Aspose.Email - Работа с рассылками**
Чтобы создать рассылку с использованием **Aspose.Email Java для Ruby**, просто вызовите модуль **DistributionList**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

oneOffmembers = Rjb::import('com.aspose.email.MapiDistributionListMemberCollection').new

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("John R. Patrick", "JohnRPatrick@armyspy.com"))

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("Tilly Bates", "TillyBates@armyspy.com"))

dlist = Rjb::import('com.aspose.email.MapiDistributionList').new("Простая рассылка", oneOffmembers)

dlist.setBody("Тестовое тело")

dlist.setSubject("Тестовая тема")

dlist.setMileage("Тестовый пробег")

dlist.setBilling("Тестовая биллинг")

dlist.save(data_dir + "distlist.msg")

puts "Рассылка успешно сохранена."

```
## **Скачать рабочий код**
Скачайте **Работа с рассылками (Aspose.Email)** с любого из нижеупомянутых социальный coding сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)