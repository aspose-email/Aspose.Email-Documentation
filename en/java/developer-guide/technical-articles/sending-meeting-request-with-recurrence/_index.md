---
title: Sending meeting request with recurrence
type: docs
weight: 240
url: /java/sending-meeting-request-with-recurrence/
---


With Aspose.Email, it is possible to generate a meeting request with recurrence. This article explains how a meeting request can be generated with specific recurrence. Appointment Unique Id can be saved for later use for sending any update to appointment.
## **Generating Meeting Request with Recurrence**
The following code sample shows how to achieve this.



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String szUniqueId;

// Create a mail message
MailMessage msg1 = new MailMessage();
msg1.getTo().add("to@domain.com");
msg1.setFrom(new MailAddress("from@gmail.com"));

// Fill appointment object
Date startDate = sdf.parse("2013-12-01 17:00:00");
Date endDate = sdf.parse("2013-12-31 17:30:00");

// Create appointment object
Appointment agendaAppointment = new Appointment("same place", startDate, endDate, msg1.getFrom(), msg1.getTo());

// Create unique id as it will help to access this appointment later
szUniqueId = UUID.randomUUID().toString();
agendaAppointment.setUniqueId(szUniqueId);
agendaAppointment.setDescription("----------------");

// Create a weekly reccurence pattern object
WeeklyRecurrencePattern pattern1 = new WeeklyRecurrencePattern(14);

// Set weekly pattern properties like days: Mon, Tue and Thu
pattern1.setStartDays(new int[3]);
pattern1.getStartDays()[0] = CalendarDay.Monday;
pattern1.getStartDays()[1] = CalendarDay.Tuesday;
pattern1.getStartDays()[2] = CalendarDay.Thursday;
pattern1.setInterval(1);

// Set recurrence pattern for the appointment
agendaAppointment.setRecurrence(pattern1);

// Attach this appointment with mail
msg1.getAlternateViews().addItem(agendaAppointment.requestApointment());

// Create SmtpCleint
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
client.setSecurityOptions(SecurityOptions.Auto);

// Send mail with appointment request
client.send(msg1);

// Return unique id for later usage
// return szUniqueId;
~~~
## **Send Appointment Update Request**
For sending an update for previous appointment, unique id is required. Following sample code shows how this appointment update request can be sent



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
Date startDate = sdf.parse("2013-12-12 17:00:00");
Date endDate = sdf.parse("2013-12-12 17:30:00");
Appointment appUpdate = new Appointment("Different Place", startDate, endDate, new MailAddress("newcustomeronnet@gmail.com"),
        MailAddressCollection.to_MailAddressCollection("kashif.iqbal@aspose.com"));
appUpdate.setUniqueId(szUniqueId);
WeeklyRecurrencePattern pattern3 = (WeeklyRecurrencePattern) appUpdate.getRecurrence();
appUpdate.setSummary("update meeting request summary");
appUpdate.setDescription("update");
MailMessage msgUpdate = new MailMessage("newcustomeronnet@gmail.com", "kashif.iqbal@aspose.com", "06 - test email - update meeting request", "test email");
msgUpdate.addAlternateView(appUpdate.updateAppointment());
SmtpClient smtp = new SmtpClient("server.domain.com", 587, "username", "password");
smtp.send(msgUpdate);
~~~