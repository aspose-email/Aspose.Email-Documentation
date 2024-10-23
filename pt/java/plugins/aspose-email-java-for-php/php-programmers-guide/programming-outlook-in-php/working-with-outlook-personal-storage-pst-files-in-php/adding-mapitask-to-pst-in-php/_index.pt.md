---
title: "Adicionando MapiTask ao PST em PHP"
url: /pt/java/adding-mapitask-to-pst-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Adicionando MapiTask ao PST**
Para adicionar MapiTask ao PST usando **Aspose.Email Java for PHP**, simplesmente invoque o módulo **AddMapiTaskToPST**. Aqui você pode ver o código de exemplo.

**Código PHP**

``` php

 $task = new MapiTask("Para Fazer", "Basta clicar e digitar para adicionar nova tarefa", new Date(), new Date());

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

$task_folder = $pst->createPredefinedFolder("Tarefas",$standardIpmFolder->Tasks);

$task_folder->addMapiMessageItem($task);

print "MapiTask adicionada com sucesso.".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiTask ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST.php)