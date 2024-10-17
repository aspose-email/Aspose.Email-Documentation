---
title: "Trabajando con Listas de Distribución en Ruby"
url: /es/java/working-with-distribution-lists-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Trabajando con Listas de Distribución**
Para crear una lista de distribución usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **DistributionList**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

oneOffmembers = Rjb::import('com.aspose.email.MapiDistributionListMemberCollection').new

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("John R. Patrick", "JohnRPatrick@armyspy.com"))

oneOffmembers.addItem(Rjb::import('com.aspose.email.MapiDistributionListMember').new("Tilly Bates", "TillyBates@armyspy.com"))

dlist = Rjb::import('com.aspose.email.MapiDistributionList').new("Lista simple", oneOffmembers)

dlist.setBody("Cuerpo de prueba")

dlist.setSubject("Asunto de prueba")

dlist.setMileage("Kilometraje de prueba")

dlist.setBilling("Facturación de prueba")

dlist.save(data_dir + "distlist.msg")

puts "Lista de distribución guardada con éxito."

```
## **Descargar Código en Ejecución**
Descargar **Trabajando con Listas de Distribución (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/distributionlist.rb)