---
title: Creating and Saving Outlook Tasks in Ruby
ArticleTitle: Creating and Saving Outlook Tasks in Ruby
type: docs
weight: 30
url: /java/creating-and-saving-outlook-tasks-in-ruby/
---

## **Aspose.Email - Creating and Saving Outlook Tasks**
To Create Outlook Tasks using **Aspose.Email Java for Ruby**, simply invoke **CreateOutlookTask** module. Here you can see example code.

**Ruby Code**

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
## **Download Running Code**
Download **Creating and Saving Outlook Tasks (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooktask.rb)
