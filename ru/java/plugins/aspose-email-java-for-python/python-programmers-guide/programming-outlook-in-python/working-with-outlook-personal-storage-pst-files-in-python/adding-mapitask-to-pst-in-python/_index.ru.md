---
title: "Добавление MapiTask в PST на языке Python"
url: /ru/java/adding-mapitask-to-pst-in-python/
weight: 40
type: docs
---

## **Aspose.Email - добавление MapiTask в PST**
Чтобы добавить MapiTask в PST, используя **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

```python



task = self.MapiTask("To Do", "Just click and type to add task", self.Date(), self.Date())

task.setPercentComplete(20)

task.setEstimatedEffort(2000)

task.setActualEffort(20)

mapiTaskHistory = self.MapiTaskHistory()

task.setHistory(mapiTaskHistory.Assigned)

task.setLastUpdate(self.Date())

task.getUsers().setOwner("Darius")

task.getUsers().setLastAssigner("Harkness")

task.getUsers().setLastDelegate("Harkness")

mapiTaskOwnership = self.MapiTaskOwnership()

task.getUsers().setOwnership(mapiTaskOwnership.AssignersCopy)

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "TaskPST.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

task_folder = pst.createPredefinedFolder("Tasks",standardIpmFolder.Tasks)

task_folder.addMapiMessageItem(task)

print "Added MapiTask Successfully."

```
## **Загрузить рабочий код**
Download **Добавление MapiTask в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
