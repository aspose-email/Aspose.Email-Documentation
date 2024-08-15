---
title: Adding MapiTask to PST in PHP
type: docs
weight: 50
url: /java/adding-mapitask-to-pst-in-php/
---

## **Aspose.Email - Adding MapiTask to PST**
To Add MapiTask to PST using **Aspose.Email Java for PHP**, simply invoke **AddMapiTaskToPST** module. Here you can see example code.

**PHP Code**

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
## **Download Running Code**
Download **Adding MapiTask to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
