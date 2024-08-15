---
title: "Создайте повторяющуюся задачу"
url: /ru/net/create-a-recurring-task/
weight: 30
type: docs
---


## **VSTO**
Ниже приведен фрагмент кода, показывающий повторение задачи в зависимости от даты:

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

Aspose.Email для .NET позволяет создавать задачи Outlook и сохранять их в формате MSG. [MapiTask](https://apireference.aspose.com/email/net/aspose.email.mapi/mapitask) класс предоставляет ряд свойств, таких как Percentcomplete, Estimatedefort, ActualEffort, History, LastUpdate и другие, для размещения и настройки информации, необходимой для задачи Outlook. В этой статье показано, как создать, сохранить и прочитать MapiTask с диска.

{{% /alert %}}

Aspose.Email позволяет создавать повторяющиеся задачи, повторяющиеся ежедневно, еженедельно, ежемесячно или ежегодно. Следующий пример кода иллюстрирует создание задачи с еженедельным повторением.

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
## **Загрузить образец кода**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Загрузить рабочий код**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Recurring%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
