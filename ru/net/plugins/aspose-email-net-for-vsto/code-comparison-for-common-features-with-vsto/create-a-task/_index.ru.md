---
title: "Создать задачу"
url: /ru/net/create-a-task/
weight: 50
type: docs
---


## **VSTO**
Ниже приведен код для создания и сохранения задачи в Outlook:

``` cs

   // Дата операции

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
#### **Создание и сохранение задач Outlook**
Чтобы создать и сохранить задачу на диск:

1. Создайте новый объект класса MapiTask.
2. Введите информацию о свойствах задачи.
3. Сохраните задачу на диск в формате MSG.

``` cs

   MapiTask task = new MapiTask("To Do", "Просто щелкните и введите, чтобы добавить новую задачу", DateTime.Now, DateTime.Now.AddDays(3));

  task.PercentComplete = 20;

  task.EstimatedEffort = 2000;

  task.ActualEffort = 20;

  task.History = MapiTaskHistory.Assigned;

  task.LastUpdate = DateTime.Now;

  task.Users.Owner = "Darius";

  task.Users.LastAssigner = "Harkness";

  task.Users.LastDelegate = "Harkness";

  task.Users.Ownership = MapiTaskOwnership.AssignersCopy;

  task.Companies = new string[] { "company1", "company2", "company3" };

  task.Categories = new string[] { "category1", "category2", "category3" };

  task.Mileage = "Некоторые тестовые пробеги";

  task.Billing = "Тестовая информация о выставлении счетов";

  task.Users.Delegator = "Тестовый делегатор";

  task.Sensitivity = MapiSensitivity.Personal;

  task.Status = MapiTaskStatus.Complete;

  task.EstimatedEffort = 5;

  task.Save("MapiTask.msg", TaskSaveFormat.Msg);


```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Скачать работающий код**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)