---
title: "Trabajando con listas de distribución en Ruby"
url: /es/java/working-with-distribution-lists-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Trabajando con listas de distribución**
Para crear una lista de distribución mediante **Aspose.Email Java para Ruby**, simplemente invoca **DistributionList** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Trabajo con listas de distribución (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)
