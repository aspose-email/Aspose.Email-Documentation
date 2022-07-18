---
title: Create a Recurring Task
type: docs
weight: 30
url: /net/create-a-recurring-task/
---


## **VSTO**
Below is the code snippet showing recurring of task on the basis of date:

``` cs

     Outlook.TaskItem task = Application.CreateItem(

    Outlook.OlItemType.olTaskItem) as Outlook.TaskItem;

    task.Subject = "Tax Preparation";

    task.StartDate = DateTime.Parse("4/1/2007 8:00 AM");

    task.DueDate = DateTime.Parse("4/15/2007 8:00 AM");

    Outlook.RecurrencePattern pattern = task.GetRecurrencePattern();

    pattern.RecurrenceType = Outlook.OlRecurrenceType.olRecursYearly;

    pattern.PatternStartDate = DateTime.Parse("4/1/2007");

    pattern.NoEndDate = true;

    task.ReminderSet = true;

    task.ReminderTime = DateTime.Parse("4/1/2007 8:00 AM");

    task.Save();


```
## **Aspose.Email**
{{% alert color="primary" %}} 

Aspose.Email for .NET allows you to create Outlook tasks and save them to MSG format. The [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask) class provides a number of properties such as Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, and others, to accommodate and set information required for an Outlook task. This article shows how to create, save and read a MapiTask from disc.

{{% /alert %}} 

Aspose.Email allows to create a recurring task where the recurrence can be daily, weekly, monthly, or yearly. The following code sample illustrates creating a task with weekly recurrence.

``` cs

   DateTime startDate = new DateTime(2015, 04, 30, 10, 00, 00);

  MapiTask task = new MapiTask("abc", "def", startDate, startDate.AddHours(1));

  task.State = MapiTaskState.NotAssigned;

  // Set the weekly recurrence

  var rec = new MapiCalendarDailyRecurrencePattern

  {

     PatternType = MapiCalendarRecurrencePatternType.Day,

     Period = 1,

     WeekStartDay = DayOfWeek.Sunday,

     EndType = MapiCalendarRecurrenceEndType.NeverEnd,

     OccurrenceCount = 0,

  };

  task.Recurrence = rec;

  task.Save("AsposeDaily.msg", TaskSaveFormat.Msg);


```
## **Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Download Running Code**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Recurring%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
