---
title: "Назначьте встречу"
url: /ru/net/create-an-appointment/
weight: 20
type: docs
---


## **VSTO**
Ниже приведен фрагмент кода для создания и сохранения встречи:

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
Чтобы создать встречу и сохранить ее в формате ICS, необходимо выполнить следующие шаги.

1. Создайте экземпляр класса Appointment и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в приведенном выше конструкторе
   1. Attendees
   1. Description
   1. Дата окончания
   1. Location
   1. Organizer
   1. Дата начала
   1. Summary
1. Вызовите метод Save () и укажите имя и формат файла в аргументах.

Встречу можно открыть в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, встреча автоматически добавляется в календарь Outlook.

Следующие фрагменты кода создают и сохраняют встречу на диске в формате ICS.

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
## **Загрузить образец кода**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Загрузить рабочий код**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
