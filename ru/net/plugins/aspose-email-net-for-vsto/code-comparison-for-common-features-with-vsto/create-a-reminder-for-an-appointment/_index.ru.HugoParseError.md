---
title: Создание напоминания о встрече
type: docs
weight: 40
url: /net/create-a-reminder-for-an-appointment/
---


## **VSTO**
Ниже приведен фрагмент кода для создания напоминания о встрече:

``` cs

    Outlook.AppointmentItem appt = Application.CreateItem(

   Outlook.OlItemType.olAppointmentItem) as Outlook.AppointmentItem;

   appt.Subject = "Дегустация вина";

   appt.Location = "Напа, Калифорния";

   appt.Sensitivity = Outlook.OlSensitivity.olPrivate;

   appt.Start = DateTime.Parse("21/10/2006 10:00 AM");

   appt.End = DateTime.Parse("21/10/2006 3:00 PM");

   appt.ReminderSet = true;

   appt.ReminderMinutesBeforeStart = 120;

   appt.Save();


```
## **Aspose.Email**
{{% alert color="primary" %}} 

Напоминание может быть добавлено при создании встречи. Эти сигналы могут срабатывать по различным критериям, например, за n минут до начала, повторяться n раз через n интервалов. Для создания этих триггеров в скрипте, заключенном в BEGIN:VALARM и END:VALARM, можно использовать различные теги.

{{% /alert %}} 

Существует несколько вариантов, при которых напоминание может быть установлено для встречи. Ниже приведен фрагмент кода:

``` cs

   string location = "Место встречи: Комната 5";

  DateTime startDate = new DateTime(1997, 3, 18, 18, 30, 00),

  endDate = new DateTime(1997, 3, 18, 19, 30, 00);

  MailAddress organizer = new MailAddress("aaa@amail.com", "Организатор");

  MailAddressCollection attendees = new MailAddressCollection();

  attendees.Add(new MailAddress("bbb@bmail.com", "Первый участник"));

  Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

  //Звуковое напоминание, которое прозвучит в точное время и

  //повторится еще 4 раза через 15 минут:

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

   //Напоминание для отображения, которое сработает за 30 минут до

   //запланированного начала события, к которому оно

   //связано, и повторится еще 2 раза через 15 минут:

   AppointmentReminder displayReminder = new AppointmentReminder();

   ReminderDuration dur = new ReminderDuration(new TimeSpan(0, -30, 0));

   displayReminder.Trigger = new ReminderTrigger(dur, ReminderRelated.Start);

   displayReminder.Repeat = 2;

   displayReminder.Duration = new ReminderDuration(new TimeSpan(0, 15, 0));

   displayReminder.Action = ReminderAction.Display;

   displayReminder.Description = "Завтрак с исполнительной командой в 8:30 AM EST";

   target.Reminders.Add(displayReminder);

   string strDisplayReminder = @"

                BEGIN:VALARM

                ACTION:DISPLAY

                REPEAT:2

                DURATION:PT15M

                DESCRIPTION:Завтрак с исполнительной командой в 8:30 AM EST

                TRIGGER;RELATED=START:-PT30M

                END:VALARM";

    //Email-уведомление, которое сработает за 2 дня до

    //запланированной даты/времени. Оно не 

    //повторяется. Электронное письмо имеет тему, текст и ссылку на вложение.

    AppointmentReminder emailReminder = new AppointmentReminder();

    ReminderDuration dur1 = new ReminderDuration(new TimeSpan(-2, 0, 0, 0));

    emailReminder.Trigger = new ReminderTrigger(dur1, ReminderRelated.Start);

    ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");

    emailReminder.Attendees.Add(attendee);

    emailReminder.Action = ReminderAction.Email;

    emailReminder.Summary = "НАПОМНЕНИЕ: ОТПРАВИТЬ ПОВЕСТЬ ДНЯ ДЛЯ НЕДЕЛЬНОЙ ВСТРЕЧИ С ПЕРСОНАЛОМ";

    emailReminder.Description = @"Черновик повестки дня должен быть отправлен участникам на еженедельную встречу менеджеров (MGR-LIST). В приложении ссылка на шаблон

                                  документа для файла повестки дня.";

    ReminderAttachment attach1 = new ReminderAttachment(new Uri("http://host.com/templates/agenda.doc"));

    emailReminder.Attachments.Add(attach1);

    target.Reminders.Add(emailReminder);

    string strEmailReminder = @"

                BEGIN:VALARM

                ACTION:EMAIL

                DESCRIPTION:Черновик повестки дня должен быть отправлен участникам на еженедельную встречу менеджеров (MGR-LIST). В приложении ссылка на шаблон

                документа для файла повестки дня.

                SUMMARY:НАПОМНЕНИЕ: ОТПРАВИТЬ ПОВЕСТЬ ДНЯ ДЛЯ НЕДЕЛЬНОЙ ВСТРЕЧИ С ПЕРСОНАЛОМ

                TRIGGER;RELATED=START:-P2D

                ATTENDEE:mailto:john_doe@host.com

                ATTACH:http://host.com/templates/agenda.doc

                END:VALARM";

    //Процедурное напоминание, которое сработает в точную дату/время

    //и повторится еще 23 раза с интервалом в один час. Напоминание будет

    //вызывать файл процедуры.

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
## **Скачать пример кода**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Скачать работающий код**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20a%20Reminder%20for%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)