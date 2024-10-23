---
title: "Criar uma Tarefa"
url: /pt/net/criar-uma-tarefa/
weight: 50
type: docs
---


## **VSTO**
Abaixo está o código para criar e salvar uma tarefa no Outlook:

``` cs

   // Operações de data

  DateTime today = DateTime.Parse("10:00 AM");

  TimeSpan duration = TimeSpan.FromDays(1);

  DateTime tomorrow = today.Add(duration);

  Outlook.MailItem mail = Application.Session.

  GetDefaultFolder( Outlook.OlDefaultFolders.olFolderInbox).Items.Find("[MessageClass]='IPM.Note'") as Outlook.MailItem;

  mail.MarkAsTask(Outlook.OlMarkInterval.olMarkTomorrow);

  mail.TaskStartDate = today;

  mail.ReminderSet = true;

  mail.ReminderTime = tomorrow;

  mail.Save();


```
## **Aspose.Email**
#### **Criando e Salvando Tarefas do Outlook**
Para criar e salvar uma tarefa no disco:

1. Instancie um novo objeto da classe MapiTask.
2. Insira informações sobre as propriedades da tarefa.
3. Salve a tarefa no disco em formato MSG.

``` cs

   MapiTask task = new MapiTask("A Fazer", "Basta clicar e digitar para adicionar nova tarefa", DateTime.Now, DateTime.Now.AddDays(3));

  task.PercentComplete = 20;

  task.EstimatedEffort = 2000;

  task.ActualEffort = 20;

  task.History = MapiTaskHistory.Assigned;

  task.LastUpdate = DateTime.Now;

  task.Users.Owner = "Darius";

  task.Users.LastAssigner = "Harkness";

  task.Users.LastDelegate = "Harkness";

  task.Users.Ownership = MapiTaskOwnership.AssignersCopy;

  task.Companies = new string[] { "empresa1", "empresa2", "empresa3" };

  task.Categories = new string[] { "categoria1", "categoria2", "categoria3" };

  task.Mileage = "Alguma quilometragem de teste";

  task.Billing = "Informações de cobrança de teste";

  task.Users.Delegator = "Test Delegator";

  task.Sensitivity = MapiSensitivity.Personal;

  task.Status = MapiTaskStatus.Complete;

  task.EstimatedEffort = 5;

  task.Save("MapiTask.msg", TaskSaveFormat.Msg);


```
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Baixar Código em Execução**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Criar%20Uma%20Tarefa)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)