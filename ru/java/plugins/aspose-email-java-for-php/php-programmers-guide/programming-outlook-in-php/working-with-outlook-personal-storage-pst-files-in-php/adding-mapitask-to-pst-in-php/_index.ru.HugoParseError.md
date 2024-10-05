---
title: Добавление MapiTask в PST на PHP
type: docs
weight: 50
url: /java/adding-mapitask-to-pst-in-php/
---

## **Aspose.Email - Добавление MapiTask в PST**
Чтобы добавить MapiTask в PST с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **AddMapiTaskToPST**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 $task = new MapiTask("To Do", "Просто щелкните и введите, чтобы добавить новую задачу", new Date(), new Date());

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

print "Успешно добавлен MapiTask.".PHP_EOL;

```
## **Скачать работающий код**
Скачайте **Добавление MapiTask в PST (Aspose.Email)** с любого из нижеупомянутых социальных coding сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)