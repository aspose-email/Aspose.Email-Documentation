---
title: "Agregar MapiTask a PST en PHP"
url: /es/java/adding-mapitask-to-pst-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Agregar MapiTask a PST**
Para agregar MapiTask a PST usando **Aspose.Email Java para PHP**, simplemente invoca **AddMapiTaskToPST** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 $task = new MapiTask("To Do", "Just click and type to add new task", new Date(), new Date());

$task->setPercentComplete(20);

$task->setEstimatedEffort(2000);

$task->setActualEffort(20);

$mapiTaskHistory=new MapiTaskHistory();

$task->setHistory($mapiTaskHistory->Assigned);

$task->setLastUpdate(new Date());

$task->getUsers()->setOwner("Darius");

$task->getUsers()->setLastAssigner("Harkness");

$task->getUsers()->setLastDelegate("Harkness");

$mapiTaskOwnership=new MapiTaskOwnership();

$task->getUsers()->setOwnership($mapiTaskOwnership->AssignersCopy);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$pst = $personalStorage->create($dataDir . "TaskPST.pst", $fileFormatVersion->Unicode);

$standardIpmFolder=new StandardIpmFolder();

$task_folder = $pst->createPredefinedFolder("Tasks",$standardIpmFolder->Tasks);

$task_folder->addMapiMessageItem($task);

print "Added MapiTask Successfully.".PHP_EOL;

```
## **Descargar Running Code**
Download **Agregar MapiTask a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
