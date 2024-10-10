---
title: "Добавление MapiTask в PST на Ruby"
url: /ru/java/adding-mapitask-to-pst-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Добавление MapiTask в PST**
Чтобы добавить MapiTask в PST с помощью **Aspose.Email Java для Ruby**, просто вызовите модуль **AddMapiTaskToPST**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

task = Rjb::import('com.aspose.email.MapiTask').new("To Do", "Просто щелкните и введите, чтобы добавить новую задачу", Rjb::import('java.util.Date').new, Rjb::import('java.util.Date').new)

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

puts "Добавление MapiTask прошло успешно."

```
## **Скачать рабочий код**
Скачать **Добавление MapiTask в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapitasktopst.rb)