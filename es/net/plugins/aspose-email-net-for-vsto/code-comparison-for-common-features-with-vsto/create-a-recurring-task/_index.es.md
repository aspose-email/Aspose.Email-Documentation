---
title: "Crear una tarea recurrente"
url: /es/net/create-a-recurring-task/
weight: 30
type: docs
---


## **VSTO**
A continuación se muestra el fragmento de código que muestra la repetición de la tarea en función de la fecha:

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

Aspose.Email para.NET permite crear tareas de Outlook y guardarlas en formato MSG. El [MapiTask](https://apireference.aspose.com/email/net/aspose.email.mapi/mapitask) La clase proporciona varias propiedades, como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate y otras, para acomodar y configurar la información requerida para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un MapiTask desde un disco.

{{% /alert %}}

Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. El siguiente ejemplo de código ilustra la creación de una tarea con periodicidad semanal.

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
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar Running Code**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Recurring%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
