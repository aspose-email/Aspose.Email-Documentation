---
title: Adding MapiTask to PST in Ruby
type: docs
weight: 60
url: /java/adding-mapitask-to-pst-in-ruby/
---

## **Aspose.Email - Adding MapiTask to PST**
To Add MapiTask to PST using **Aspose.Email Java for Ruby**, simply invoke **AddMapiTaskToPST** module. Here you can see example code.

**Ruby Code**

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
## **Download Running Code**
Download **Adding MapiTask to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapitasktopst.rb)
