---
title: "Creando y Guardando Tareas de Outlook en Ruby"
url: /es/java/creando-y-guardando-tareas-de-outlook-en-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Creando y Guardando Tareas de Outlook**
Para crear tareas de Outlook utilizando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **CreateOutlookTask**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

contact = Rjb::import('com.aspose.email.MapiContact').new

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

calendar.set(2012, calendar.NOVEMBER, 1, 0, 0, 0)

startDate = calendar.getTime()

calendar.set(2012, calendar.DECEMBER, 1)

endDate = calendar.getTime()

task = Rjb::import('com.aspose.email.MapiTask').new("Para Hacer", "Simplemente haz clic y escribe para añadir una nueva tarea", startDate, endDate)

task.setPercentComplete(20)

task.setEstimatedEffort(2000)

task.setActualEffort(20)

task.setHistory(Rjb::import('com.aspose.email.MapiTaskHistory').Assigned)

task.getUsers().setOwner("Darius")

task.getUsers().setLastAssigner("Harkness")

task.getUsers().setLastDelegate("Harkness")

task.getUsers().setOwnership(Rjb::import('com.aspose.email.MapiTaskOwnership').AssignersCopy)

companies = ["empresa1", "empresa2", "empresa3"]

task.setCompanies(companies)

categories = ["categoría1", "categoría2", "categoría3"]

task.setCategories(categories)

task.setMileage("Algún kilometraje de prueba")

task.setBilling("Información de facturación de prueba")

task.getUsers().setDelegator("Delegador de Prueba")

task.setSensitivity(Rjb::import('com.aspose.email.MapiSensitivity').Personal)

task.setStatus(Rjb::import('com.aspose.email.MapiTaskStatus').Complete)

task.save(data_dir + "MapiTask.msg", Rjb::import('com.aspose.email.TaskSaveFormat').Msg)

puts "Tarea de Outlook creada exitosamente."

```
## **Descargar Código en Ejecución**
Descarga **Creando y Guardando Tareas de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooktask.rb)