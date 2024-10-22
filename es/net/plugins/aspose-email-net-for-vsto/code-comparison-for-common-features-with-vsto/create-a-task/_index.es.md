---
title: "Crear una Tarea"
url: /es/net/create-a-task/
weight: 50
type: docs
---


## **VSTO**
A continuación se muestra el código para crear y guardar una tarea en Outlook:

``` cs

   // Operaciones de fecha

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
#### **Creando y Guardando Tareas de Outlook**
Para crear y guardar una tarea en el disco:

1. Instanciar un nuevo objeto de la clase MapiTask.
2. Ingresar la información de las propiedades de la tarea.
3. Guardar la tarea en el disco en formato MSG.

``` cs

   MapiTask task = new MapiTask("Por Hacer", "Simplemente haz clic y escribe para agregar una nueva tarea", DateTime.Now, DateTime.Now.AddDays(3));

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

  task.Categories = new string[] { "categoría1", "categoría2", "categoría3" };

  task.Mileage = "Algún kilometraje de prueba";

  task.Billing = "Información de facturación de prueba";

  task.Users.Delegator = "Delegador de prueba";

  task.Sensitivity = MapiSensitivity.Personal;

  task.Status = MapiTaskStatus.Complete;

  task.EstimatedEffort = 5;

  task.Save("MapiTask.msg", TaskSaveFormat.Msg);


```
## **Descargar Código de Ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar Código en Ejecución**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Task)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)