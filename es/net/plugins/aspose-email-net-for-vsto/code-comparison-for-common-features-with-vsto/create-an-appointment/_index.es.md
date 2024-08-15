---
title: "Crea una cita"
url: /es/net/create-an-appointment/
weight: 20
type: docs
---


## **VSTO**
A continuación se muestra el fragmento de código para crear y guardar una cita:

``` cs

   Outlook.AppointmentItem appt = Application.CreateItem(

  Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

  appt.Subject = "Developer's Conference";

  appt.AllDayEvent = true;

  appt.Start = DateTime.Parse("6/11/2007 12:00 AM");

  appt.End = DateTime.Parse("6/16/2007 12:00 AM");

  appt.Display(false);


```
## **Aspose.Email**
Se requieren los siguientes pasos para crear una cita y guardarla en formato ICS.

1. Crea una instancia de la clase Appointment e inicialízala con este constructor.
1. Pase los siguientes argumentos en el constructor anterior
   1. Attendees
   1. Description
   1. Fecha de finalización
   1. Location
   1. Organizer
   1. Fecha de inicio
   1. Summary
1. Llame al método Save () y especifique el nombre y el formato del archivo en los argumentos.

La cita se puede abrir en Microsoft Outlook o en cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, agrega automáticamente la cita al calendario de Outlook.

Los siguientes fragmentos de código crean y guardan una cita en el disco en formato ICS.

``` cs

   string location = "Meeting Location: Room 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Organizer");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "First attendee"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  target.Save("savedFile.ics");


```
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar Running Code**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
