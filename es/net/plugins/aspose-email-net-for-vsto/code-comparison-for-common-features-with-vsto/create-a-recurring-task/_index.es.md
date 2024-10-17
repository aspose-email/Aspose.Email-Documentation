---
title: "Crear una Tarea Recurrente"
url: /es/net/create-a-recurring-task/
weight: 30
type: docs
---


## **VSTO**
A continuación se muestra el fragmento de código que muestra la recurrencia de una tarea en función de la fecha:

``` cs

     Outlook.TaskItem task = Application.CreateItem(

    Outlook.OlItemType.olTaskItem) as Outlook.TaskItem;

    task.Subject = "Preparación de Impuestos";

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

Aspose.Email para .NET permite crear tareas de Outlook y guardarlas en formato MSG. La clase [MapiTask](https://apireference.aspose.com/email/net/aspose.email.mapi/mapitask) proporciona una serie de propiedades como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, y otras, para acomodar y establecer la información necesaria para una tarea de Outlook. Este artículo muestra cómo crear, guardar y leer un MapiTask desde el disco.

{{% /alert %}} 

Aspose.Email permite crear una tarea recurrente donde la recurrencia puede ser diaria, semanal, mensual o anual. El siguiente ejemplo de código ilustra la creación de una tarea con recurrencia semanal.

``` cs

   DateTime startDate = new DateTime(2015, 04, 30, 10, 00, 00);

  MapiTask task = new MapiTask("abc", "def", startDate, startDate.AddHours(1));

  task.State = MapiTaskState.NotAssigned;

  // Establecer la recurrencia semanal

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
## **Descargar Código de Ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar Código en Ejecución**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Recurring%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)