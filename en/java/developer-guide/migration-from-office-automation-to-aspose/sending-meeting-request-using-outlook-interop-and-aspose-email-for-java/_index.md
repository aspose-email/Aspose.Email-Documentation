---
title: Sending Meeting Request Using Outlook Interop and Aspose.Email for Java
ArticleTitle: Sending Meeting Request Using Outlook Interop and Aspose.Email for Java
type: docs
weight: 40
url: /java/sending-meeting-request-using-outlook-interop-and-aspose-email-for-java/
---


{{% alert color="primary" %}} 

Our migration tips show how Aspose products can be used to improve your applications and free you from dependency on traditional automation.

This migration tip sends a meeting request to a recipient. It is demonstrates how to send meeting request in two ways:

- [Using Outlook Interop](#sending-meeting-request-with-outlook-interop).
- [Using Aspose.Email for Java](#advantages-of-using-asposeemail-for-java).

We'll also discuss the advantages of the latter approach.

{{% /alert %}} 
## **Sending Meeting Request with Outlook Interop**
To use Outlook classes, Outlook.Interop must be referenced in your .NET project. The code snippet below:

1. Creates a meeting request.
1. Sets properties like subject, body, location and time.
1. Sends the meeting request to the recipient.

Microsoft Outlook must be installed on the system where this sample application will run.
### **Programming Samples**
**C#**

~~~cs

// Create an instance of Outlook Application class

Outlook.Application outlookApp = new Outlook.Application ();

// Create an instance of AppointmentItem object and set the properties:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem) outlookApp.CreateItem (Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "subject of appointment";

oAppointment.Body = "body text of appointment";

oAppointment.Location = "Appointment location";

// Set the start date and end dates

oAppointment.Start = Convert.ToDateTime ("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Save the appointment

oAppointment.Save ();

// Send the appointment

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal ();

mailItem.To = "recipient@domain.com";

mailItem.Send();


~~~
## **Sending Meeting Request using Aspose.Email for Java**
The code below uses Aspose.Email for Java to send a meeting request. First, create the meeting request using the [Aspose.Email Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) class. Then send the email, attach the meeting request and send the email using the [Aspose.Email SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient) class.
### **Advantages of using Aspose.Email for Java**
Outlook Interop requires Microsoft Outlook to be installed on the system where it is used. Aspose.Email for Java does not require Microsoft Outlook to be installed and is suitable in server applications.
### **Programming Samples**

~~~Java

// Create attendees of the meeting
MailAddressCollection attendees = new MailAddressCollection();
attendees.add("recipient1@domain.com");
attendees.add("recipient2@domain.com");

java.util.Calendar c = java.util.Calendar.getInstance();
Date startDate = c.getTime();
c.add(java.util.Calendar.HOUR_OF_DAY, 1);
Date endDate = c.getTime();

// Set up appointment
Appointment app = new Appointment(
    "Location", // location of meeting
    startDate, // start date
    endDate, // end date
    new MailAddress("organizer@domain.com"), // organizer
    attendees); // attendees

// Set up message that needs to be sent
MailMessage msg = new MailMessage();
msg.setFrom(new MailAddress("from@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setSubject("appointment request");
msg.setBody("you are invited");

// Add meeting request to the message
msg.addAlternateView(app.requestApointment());

// Set up the SMTP client to send email with meeting request
try (SmtpClient client = new SmtpClient("host", 25, "user", "password")) {
    client.send(msg);
}

~~~
