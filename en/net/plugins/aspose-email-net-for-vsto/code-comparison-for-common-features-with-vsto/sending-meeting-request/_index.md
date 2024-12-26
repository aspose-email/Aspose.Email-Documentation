---
title: Sending Meeting Request
ArticleTitle: Sending Meeting Request
type: docs
weight: 200
url: /net/sending-meeting-request/
---


## **VSTO**
To use Outlook classes, Outlook.Interop must be referenced in your .NET project. The code snippet below:

1. Creates a meeting request.
1. Sets properties like subject, body, location and time.
1. Sends the meeting request to the recipient.
1. Microsoft Outlook must be installed on the system where this sample application will run.

``` cs

 // Create an instance of Outlook Application class

Outlook.Application outlookApp = new Outlook.Application();

// Create an instance of AppointmentItem object and set the properties:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem)outlookApp.CreateItem(Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "subject of appointment";

oAppointment.Body = "body text of appointment";

oAppointment.Location = "Appointment location";

// Set the start date and end dates

oAppointment.Start = Convert.ToDateTime("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Save the appointment

oAppointment.Save();

// Send the appointment

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal();

mailItem.To = "recipient@domain.com";

mailItem.Send();

```
## **Aspose.Email**
The code below uses Aspose.Email for .NET to send a meeting request. First, create the meeting request using the Aspose.Email.Appointment class. Then send the email, attach the meeting request and send the email using the Aspose.Email.Mail.SmtpClient class.

Advantages of using Aspose.Email for .NET

Outlook Interop requires Microsoft Outlook to be installed on the system where it is used. Aspose.Email for .NET does not require Microsoft Outlook to be installed and is suitable in server applications.

``` cs

  // Create attendees of the meeting

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Set up appointment

Appointment app = new Appointment(

    "Location", // location of meeting

    DateTime.Now, // start date

    DateTime.Now.AddHours(1), // end date

    new MailAddress("organizer@domain.com"), // organizer

    attendees); // attendees

// Set up message that needs to be sent

MailMessage msg = new MailMessage();

msg.From = "from@domain.com";

msg.To = "to@domain.com";

msg.Subject = "appointment request";

msg.Body = "you are invited";

// Add meeting request to the message

msg.AddAlternateView(app.RequestApointment());

// Set up the SMTP client to send email with meeting request

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");

client.Send(msg);

```
##**Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772944)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Sending.Meeting.Request.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Sending%20Meeting%20Request%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Sending%20Meeting%20Request%20\(Aspose.Email\).zip)
