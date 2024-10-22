---
title: "Adicionando MapiTask ao PST em Python"
url: /pt/java/adicionando-mapitask-ao-pst-em-python/
weight: 40
type: docs
---

## **Aspose.Email - Adicionando MapiTask ao PST**
Para adicionar MapiTask ao PST usando **Aspose.Email Java para Python**, utilize o seguinte código.

**Código Python**

```python



task = self.MapiTask("A Fazer", "Basta clicar e digitar para adicionar a tarefa", self.Date(), self.Date())

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

task_folder = pst.createPredefinedFolder("Tarefas",standardIpmFolder.Tasks)

task_folder.addMapiMessageItem(task)

print "MapiTask adicionado com sucesso."

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiTask ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)