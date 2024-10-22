---
title: "Crear una Cita"
url: /es/net/crear-una-cita/
weight: 20
type: docs
---


## **VSTO**
A continuación se muestra el fragmento de código para crear y guardar una cita:

``` cs

   Outlook.AppointmentItem appt = Application.CreateItem(

  Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

  appt.Subject = "Conferencia de Desarrolladores";

  appt.AllDayEvent = true;

  appt.Start = DateTime.Parse("11/6/2007 12:00 AM");

  appt.End = DateTime.Parse("16/6/2007 12:00 AM");

  appt.Display(false);


```
## **Aspose.Email**
Los siguientes pasos son necesarios para crear una cita y guardarla en formato ICS.

1. Crear una instancia de la clase Appointment e inicializarla con este constructor.
1. Pasar los siguientes argumentos en el constructor anterior 
   1. Asistentes
   1. Descripción
   1. Fecha de Finalización
   1. Ubicación
   1. Organizador
   1. Fecha de Inicio
   1. Resumen
1. Llamar al método Save() y especificar el nombre del archivo y el formato en los argumentos.

La cita se puede abrir en Microsoft Outlook o en cualquier programa que pueda cargar un archivo ICS. Si se abre el archivo en Microsoft Outlook, automáticamente se agrega la cita al calendario de Outlook.

Los siguientes fragmentos de código crean y guardan una cita en el disco en formato ICS.

``` cs

   string location = "Ubicación de la Reunión: Sala 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "Primer asistente"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  target.Save("savedFile.ics");


```
## **Descargar Código de Ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar Código en Ejecución**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Crear%20una%20Cita)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)