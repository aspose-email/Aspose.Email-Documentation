---
title: "Añadiendo MapiTask a PST en Ruby"
url: /es/java/adding-mapitask-to-pst-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Añadiendo MapiTask a PST**
Para añadir MapiTask a PST usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **AddMapiTaskToPST**. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

task = Rjb::import('com.aspose.email.MapiTask').new("To Do", "Solo haz clic y escribe para añadir nueva tarea", Rjb::import('java.util.Date').new, Rjb::import('java.util.Date').new)

task.setPercentComplete(20)

task.setEstimatedEffort(2000)

task.setActualEffort(20)

task.setHistory(Rjb::import('com.aspose.email.MapiTaskHistory').Assigned)

task.setLastUpdate(Rjb::import('java.util.Date').new)

task.getUsers().setOwner("Darius")

task.getUsers().setLastAssigner("Harkness")

task.getUsers().setLastDelegate("Harkness")

task.getUsers().setOwnership(Rjb::import('com.aspose.email.MapiTaskOwnership').AssignersCopy)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "TaskPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

task_folder = pst.createPredefinedFolder("Tasks", Rjb::import('com.aspose.email.StandardIpmFolder').Tasks)

task_folder.addMapiMessageItem(task)

puts "Añadido MapiTask con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Añadiendo MapiTask a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapitasktopst.rb)