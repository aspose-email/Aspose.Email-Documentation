---
title: "Criar uma Tarefa Recorrente"
url: /pt/net/create-a-recurring-task/
weight: 30
type: docs
---

## **VSTO**
Abaixo está o código que mostra a recorrência de uma tarefa com base na data:

``` cs

     Outlook.TaskItem task = Application.CreateItem(

    Outlook.OlItemType.olTaskItem) as Outlook.TaskItem;

    task.Subject = "Preparação de Impostos";

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

Aspose.Email para .NET permite que você crie tarefas do Outlook e as salve no formato MSG. A classe [MapiTask](https://apireference.aspose.com/email/net/aspose.email.mapi/mapitask) fornece uma série de propriedades como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, entre outras, para acomodar e definir informações necessárias para uma tarefa do Outlook. Este artigo mostra como criar, salvar e ler um MapiTask do disco.

{{% /alert %}} 

Aspose.Email permite criar uma tarefa recorrente onde a recorrência pode ser diária, semanal, mensal ou anual. O seguinte exemplo de código ilustra a criação de uma tarefa com recorrência semanal.

``` cs

   DateTime startDate = new DateTime(2015, 04, 30, 10, 00, 00);

  MapiTask task = new MapiTask("abc", "def", startDate, startDate.AddHours(1));

  task.State = MapiTaskState.NotAssigned;

  // Definir a recorrência semanal

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
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Baixar Código em Execução**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Recurring%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)