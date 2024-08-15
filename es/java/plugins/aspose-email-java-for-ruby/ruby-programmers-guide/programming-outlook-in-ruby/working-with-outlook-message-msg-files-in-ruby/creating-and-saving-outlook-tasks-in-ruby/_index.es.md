---
title: "Crear y guardar tareas de Outlook en Ruby"
url: /es/java/creating-and-saving-outlook-tasks-in-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Creación y almacenamiento de tareas de Outlook**
Para crear tareas de Outlook mediante **Aspose.Email Java para Ruby**, simplemente invoca **CreateOutlookTask** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

contact = Rjb::import('com.aspose.email.MapiContact').new

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

calendar.set(2012, calendar.NOVEMBER, 1, 0, 0, 0)

startDate = calendar.getTime()

calendar.set(2012, calendar.DECEMBER, 1)

endDate = calendar.getTime()

task = Rjb::import('com.aspose.email.MapiTask').new("To Do", "Just click and type to add new task", startDate, endDate)

task.setPercentComplete(20)

task.setEstimatedEffort(2000)

task.setActualEffort(20)

task.setHistory(Rjb::import('com.aspose.email.MapiTaskHistory').Assigned)

task.getUsers().setOwner("Darius")

task.getUsers().setLastAssigner("Harkness")

task.getUsers().setLastDelegate("Harkness")

task.getUsers().setOwnership(Rjb::import('com.aspose.email.MapiTaskOwnership').AssignersCopy)

companies = ["company1", "company2", "company3"]

task.setCompanies(companies)

categories = ["category1", "category2", "category3"]

task.setCategories(categories)

task.setMileage("Some test mileage")

task.setBilling("Test billing information")

task.getUsers().setDelegator("Test Delegator")

task.setSensitivity(Rjb::import('com.aspose.email.MapiSensitivity').Personal)

task.setStatus(Rjb::import('com.aspose.email.MapiTaskStatus').Complete)

task.save(data_dir + "MapiTask.msg", Rjb::import('com.aspose.email.TaskSaveFormat').Msg)

puts "Created outlook task successfully."

```
## **Descargar Running Code**
Download **Creación y almacenamiento de tareas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooktask.rb)
