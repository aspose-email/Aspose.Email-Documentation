---
title: "Criando e Salvando Tarefas do Outlook em Ruby"
url: /pt/java/creating-and-saving-outlook-tasks-in-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Criando e Salvando Tarefas do Outlook**
Para criar tarefas do Outlook usando **Aspose.Email Java para Ruby**, basta invocar o módulo **CreateOutlookTask**. Aqui você pode ver um código de exemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

contact = Rjb::import('com.aspose.email.MapiContact').new

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

calendar.set(2012, calendar.NOVEMBER, 1, 0, 0, 0)

startDate = calendar.getTime()

calendar.set(2012, calendar.DECEMBER, 1)

endDate = calendar.getTime()

task = Rjb::import('com.aspose.email.MapiTask').new("To Do", "Basta clicar e digitar para adicionar nova tarefa", startDate, endDate)

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

task.setMileage("Alguma quilometragem de teste")

task.setBilling("Informações de cobrança de teste")

task.getUsers().setDelegator("Test Delegator")

task.setSensitivity(Rjb::import('com.aspose.email.MapiSensitivity').Personal)

task.setStatus(Rjb::import('com.aspose.email.MapiTaskStatus').Complete)

task.save(data_dir + "MapiTask.msg", Rjb::import('com.aspose.email.TaskSaveFormat').Msg)

puts "Tarefa do Outlook criada com sucesso."

```
## **Baixar Código em Execução**
Baixar **Criando e Salvando Tarefas do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooktask.rb)