---
title: "Crie um Lembrete para um Compromisso"
url: /pt/net/create-a-reminder-for-an-appointment/
weight: 40
type: docs
---


## **VSTO**
Abaixo está o fragmento de código para criar um lembrete para um compromisso:

``` cs

    Outlook.AppointmentItem appt = Application.CreateItem(

   Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

   appt.Subject = "Degustação de Vinhos";

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

Um lembrete pode ser adicionado quando um compromisso é criado. Esses alarmes podem ser acionados com base em diferentes critérios, como n minutos antes do horário agendado, repetir n vezes em n intervalos. Diferentes tags podem ser usadas para criar esses gatilhos no script cercado por BEGIN:VALARM e END:VALARM dentro de um compromisso.

{{% /alert %}} 

Existem várias variantes nas quais o lembrete pode ser configurado em um compromisso. Abaixo está o fragmento de código:

``` cs

   string location = "Localização da Reunião: Sala 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "Primeiro participante"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  //Alarme de áudio que soará em um horário preciso e

  //repetirá mais 4 vezes em intervalos de 15 minutos:

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

   //Alarme de exibição que será acionado 30 minutos antes do

   //início agendado do evento com o qual está

   //associado e se repetirá mais 2 vezes em intervalos de 15 minutos:

   AppointmentReminder displayReminder = new AppointmentReminder();

   ReminderDuration dur = new ReminderDuration(new TimeSpan(0, -30, 0));

   displayReminder.Trigger = new ReminderTrigger(dur, ReminderRelated.Start);

   displayReminder.Repeat = 2;

   displayReminder.Duration = new ReminderDuration(new TimeSpan(0, 15, 0));

   displayReminder.Action = ReminderAction.Display;

   displayReminder.Description = "Reunião de café da manhã com a equipe executiva às 8:30 AM EST";

   target.Reminders.Add(displayReminder);

   string strDisplayReminder = @"

                BEGIN:VALARM

                ACTION:DISPLAY

                REPEAT:2

                DURATION:PT15M

                DESCRIPTION:Reunião de café da manhã com a equipe executiva às 8:30 AM EST

                TRIGGER;RELATED=START:-PT30M

                END:VALARM";

    //Alarme de e-mail que será acionado 2 dias antes da

    //data/hora de vencimento agendada. Ele não

    //se repete. O e-mail tem um assunto, corpo e link de anexo.

    AppointmentReminder emailReminder = new AppointmentReminder();

    ReminderDuration dur1 = new ReminderDuration(new TimeSpan(-2, 0, 0, 0));

    emailReminder.Trigger = new ReminderTrigger(dur1, ReminderRelated.Start);

    ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");

    emailReminder.Attendees.Add(attendee);

    emailReminder.Action = ReminderAction.Email;

    emailReminder.Summary = "LEMBRETE: ENVIAR AGENDA PARA A REUNIÃO SEMANAL DA EQUIPE";

    emailReminder.Description = @"Uma agenda preliminar precisa ser enviada aos participantes da reunião semanal dos gerentes (MGR-LIST). Anexo está um link para o

                                  modelo de documento para o arquivo de agenda.";

    ReminderAttachment attach1 = new ReminderAttachment(new Uri("http://host.com/templates/agenda.doc"));

    emailReminder.Attachments.Add(attach1);

    target.Reminders.Add(emailReminder);

    string strEmailReminder = @"

                BEGIN:VALARM

                ACTION:EMAIL

                DESCRIPTION:Uma agenda preliminar precisa ser enviada aos participantes da reunião semanal dos gerentes (MGR-LIST). Anexo está um link para o documento

                modelo para o arquivo de agenda.

                SUMMARY:LEMBRETE: ENVIAR AGENDA PARA A REUNIÃO SEMANAL DA EQUIPE

                TRIGGER;RELATED=START:-P2D

                ATTENDEE:mailto:john_doe@host.com

                ATTACH:http://host.com/templates/agenda.doc

                END:VALARM";

    //Alarme procedimental que será acionado em uma data/hora precisa

    //e se repetirá mais 23 vezes em intervalos de uma hora. O alarme irá

    //invocar um arquivo de procedimento.

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
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Baixar Código em Execução**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Reminder%20for%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)