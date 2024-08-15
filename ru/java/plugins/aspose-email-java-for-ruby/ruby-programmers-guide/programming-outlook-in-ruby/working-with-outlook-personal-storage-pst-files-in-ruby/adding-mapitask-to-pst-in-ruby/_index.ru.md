---
title: "Добавление MapiTask в PST в Ruby"
url: /ru/java/adding-mapitask-to-pst-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - добавление MapiTask в PST**
Чтобы добавить MapiTask в PST, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **AddMapiTaskToPST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

task = Rjb::import('com.aspose.email.MapiTask').new("To Do", "Just click and type to add new task", Rjb::import('java.util.Date').new, Rjb::import('java.util.Date').new)

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

puts "Added MapiTask Successfully."

```
## **Загрузить рабочий код**
Download **Добавление MapiTask в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapitasktopst.rb)
