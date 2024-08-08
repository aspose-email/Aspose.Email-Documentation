---
title: Adding MapiTask to PST in Python
type: docs
weight: 40
url: /java/adding-mapitask-to-pst-in-python/
---

## **Aspose.Email - Adding MapiTask to PST**
To Add MapiTask to PST using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



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

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiTask to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
