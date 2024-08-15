---
title: "Добавление MapiTask в PST в PHP"
url: /ru/java/adding-mapitask-to-pst-in-php/
weight: 50
type: docs
---

## **Aspose.Email - добавление MapiTask в PST**
Чтобы добавить MapiTask в PST, используя **Aspose.Электронная почта Java для PHP**, просто вызовите **AddMapiTaskToPST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

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
## **Загрузить рабочий код**
Download **Добавление MapiTask в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
