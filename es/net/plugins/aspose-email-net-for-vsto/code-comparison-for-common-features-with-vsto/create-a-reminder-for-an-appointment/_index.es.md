---
title: "Crear un recordatorio para una cita"
url: /es/net/create-a-reminder-for-an-appointment/
weight: 40
type: docs
---

## **VSTO**
A continuación se muestra el fragmento de código para crear un recordatorio para una cita:

``` cs

    Outlook.AppointmentItem appt = Application.CreateItem(

   Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

   appt.Subject = "Cata de Vinos";

   appt.Location = "Napa CA";

   appt.Sensitivity = Outlook.OlSensitivity.olPrivate;

   appt.Start = DateTime.Parse("21/10/2006 10:00 AM");

   appt.End = DateTime.Parse("21/10/2006 3:00 PM");

   appt.ReminderSet = true;

   appt.ReminderMinutesBeforeStart = 120;

   appt.Save();


```
## **Aspose.Email**
{{% alert color="primary" %}} 

Se puede añadir un recordatorio al crear una cita. Estas alarmas pueden activarse en base a diferentes criterios, como n minutos antes de que comience el horario, repetirse n veces en n intervalos. Se pueden usar diferentes etiquetas para crear estos desencadenantes en el script encerrado entre BEGIN:VALARM y END:VALARM dentro de una cita.

{{% /alert %}} 

Existen varias variantes en las que se puede establecer el recordatorio en una cita. A continuación se muestra el fragmento de código:

``` cs

   string location = "Ubicación de la reunión: Sala 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "Primer asistente"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  //Alarma de audio que sonará a una hora precisa y

  //se repetirá 4 veces más a intervalos de 15 minutos:

  AppointmentReminder audioReminder = new AppointmentReminder();

  audioReminder.Trigger = new ReminderTrigger(new DateTime(1997, 3, 17, 13, 30, 0, DateTimeKind.Utc));

  audioReminder.Repeat = 4;

  audioReminder.Duration = new ReminderDuration(new TimeSpan(0, 15, 0));

  audioReminder.Action = ReminderAction.Audio;

  ReminderAttachment attach = new ReminderAttachment(new Uri("ftp://host.com/pub/sounds/bell-01.aud"));

  audioReminder.Attachments.Add(attach);

  target.Reminders.Add(audioReminder);

  string strAudioReminder = @"BEGIN:VALARM

                ACTION:AUDIO

                REPEAT:4

                DURATION:PT15M

                TRIGGER;VALUE=DATE-TIME:19970317T133000Z

                ATTACH:ftp://host.com/pub/sounds/bell-01.aud

                END:VALARM";

   //Alarma de visualización que se activará 30 minutos antes de la

   //hora programada para el inicio del evento al que está

   //asociada y se repetirá 2 veces más a intervalos de 15 minutos:

   AppointmentReminder displayReminder = new AppointmentReminder();

   ReminderDuration dur = new ReminderDuration(new TimeSpan(0, -30, 0));

   displayReminder.Trigger = new ReminderTrigger(dur, ReminderRelated.Start);

   displayReminder.Repeat = 2;

   displayReminder.Duration = new ReminderDuration(new TimeSpan(0, 15, 0));

   displayReminder.Action = ReminderAction.Display;

   displayReminder.Description = "Reunión de desayuno con el equipo ejecutivo a las 8:30 AM EST";

   target.Reminders.Add(displayReminder);

   string strDisplayReminder = @"

                BEGIN:VALARM

                ACTION:DISPLAY

                REPEAT:2

                DURATION:PT15M

                DESCRIPTION:Reunión de desayuno con el equipo ejecutivo a las 8:30 AM EST

                TRIGGER;RELATED=START:-PT30M

                END:VALARM";

    //Alarma de correo electrónico que se activará 2 días antes de la

    //fecha/hora de vencimiento programada. No se

    //repite. El correo electrónico tiene un asunto, cuerpo y enlace de archivo adjunto.

    AppointmentReminder emailReminder = new AppointmentReminder();

    ReminderDuration dur1 = new ReminderDuration(new TimeSpan(-2, 0, 0, 0));

    emailReminder.Trigger = new ReminderTrigger(dur1, ReminderRelated.Start);

    ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");

    emailReminder.Attendees.Add(attendee);

    emailReminder.Action = ReminderAction.Email;

    emailReminder.Summary = "RECORDATORIO: ENVIAR AGENDA PARA LA REUNIÓN SEMANAL DEL PERSONAL";

    emailReminder.Description = @"Se debe enviar un borrador de agenda a los asistentes de la reunión semanal de gerentes (MGR-LIST). Adjunto se encuentra un enlace al

                                  documento plantilla para el archivo de agenda.";

    ReminderAttachment attach1 = new ReminderAttachment(new Uri("http://host.com/templates/agenda.doc"));

    emailReminder.Attachments.Add(attach1);

    target.Reminders.Add(emailReminder);

    string strEmailReminder = @"

                BEGIN:VALARM

                ACTION:EMAIL

                DESCRIPTION:Se debe enviar un borrador de agenda a los asistentes de la reunión semanal de gerentes (MGR-LIST). Adjunto se encuentra un enlace al documento

                plantilla para el archivo de agenda.

                SUMMARY:RECORDATORIO: ENVIAR AGENDA PARA LA REUNIÓN SEMANAL DEL PERSONAL

                TRIGGER;RELATED=START:-P2D

                ATTENDEE:mailto:john_doe@host.com

                ATTACH:http://host.com/templates/agenda.doc

                END:VALARM";

    //Alarma procedimental que se activará en una fecha/hora precisas

    //y se repetirá 23 veces más a intervalos de una hora. La alarma

    //invocará un archivo de procedimiento.

    AppointmentReminder procReminder = new AppointmentReminder();

    procReminder.Trigger = new ReminderTrigger(new DateTime(1998, 1, 1, 5, 0, 0, DateTimeKind.Utc));

    procReminder.Repeat = 23;

    procReminder.Duration = new ReminderDuration(new TimeSpan(1, 0, 0));

    procReminder.Action = ReminderAction.Procedure;

    ReminderAttachment attach2 = new ReminderAttachment(new Uri("ftp://host.com/novo-procs/felizano.exe"));

    procReminder.Attachments.Add(attach2);

    target.Reminders.Add(procReminder);

    string strProcReminder = @"

                BEGIN:VALARM

                ACTION:PROCEDURE

                REPEAT:23

                DURATION:PT1H

                TRIGGER;VALUE=DATE-TIME:19980101T050000Z

                ATTACH:ftp://host.com/novo-procs/felizano.exe

                END:VALARM";

    target.Save("savedFile.ics");


```
## **Descargar código de ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Descargar código en ejecución**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Reminder%20for%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)