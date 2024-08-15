---
title: Create a Task
type: docs
weight: 50
url: /net/create-a-task/
---


## **VSTO**
Below is the code for creating and saving task in Outlook:

``` cs

   // Date operations

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
#### **Creating and Saving Outlook Tasks**
To create and save a task to disc:

1. Instantiate a new object of the MapiTask class.
2. Enter task property information.
3. Save the task to disc in MSG format.

``` cs

   MapiTask task = new MapiTask("To Do", "Just click and type to add new task", DateTime.Now, DateTime.Now.AddDays(3));

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

  task.Mileage = "Some test mileage";

  task.Billing = "Test billing information";

  task.Users.Delegator = "Test Delegator";

  task.Sensitivity = MapiSensitivity.Personal;

  task.Status = MapiTaskStatus.Complete;

  task.EstimatedEffort = 5;

  task.Save("MapiTask.msg", TaskSaveFormat.Msg);


```
## **Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Download Running Code**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
