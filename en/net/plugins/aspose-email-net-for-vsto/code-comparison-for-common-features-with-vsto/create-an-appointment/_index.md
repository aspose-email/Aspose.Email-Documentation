---
title: Create an Appointment
type: docs
weight: 20
url: /net/create-an-appointment/
---


## **VSTO**
Below is the code snippet to create and save an appointment:

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
Following steps are required to create an appointment and save it in ICS format.

1. Create an instance of the Appointment class and initialize it with this constructor.
1. Pass the following arguments in the above constructor 
   1. Attendees
   1. Description
   1. End Date
   1. Location
   1. Organizer
   1. Start Date
   1. Summary
1. Call the Save() method and specify the file name and format in the arguments.

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

The following code snippets create and save an appointment to disk in ICS format.

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
## **Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Download Running Code**
- [Codeplex](https://archive.codeplex.com/?p=asposevsto#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20an%20Appointment)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
