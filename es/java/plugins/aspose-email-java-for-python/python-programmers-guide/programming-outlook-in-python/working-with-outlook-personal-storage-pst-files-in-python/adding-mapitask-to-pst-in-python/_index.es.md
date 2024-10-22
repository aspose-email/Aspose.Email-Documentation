---
title: "Agregar MapiTask a PST en Python"
url: /es/java/adding-mapitask-to-pst-in-python/
weight: 40
type: docs
---

## **Aspose.Email - Agregar MapiTask a PST**
Para agregar MapiTask a PST utilizando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código Python**

```python



task = self.MapiTask("To Do", "Solo haz clic y escribe para agregar la tarea", self.Date(), self.Date())

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

print "Mapa de tarea añadida con éxito."

```
## **Descargar código en funcionamiento**
Descarga **Agregar MapiTask a PST (Aspose.Email)** de cualquiera de los siguientes sitios de codificación social:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)