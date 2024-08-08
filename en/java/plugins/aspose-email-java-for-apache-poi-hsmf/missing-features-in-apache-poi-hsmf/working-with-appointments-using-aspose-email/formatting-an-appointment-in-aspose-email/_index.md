---
title: Formatting an Appointment in Aspose.Email
type: docs
weight: 20
url: /java/formatting-an-appointment-in-aspose-email/
---

## **Aspose.Email - Formatting an Appointment**
The AppointmentFormattingOptions class can be used to format the appointment in text and HTML format.

**Java**

``` java

 Appointment appointment = Appointment.load(dataDir + "appointment.ics");

AppointmentFormattingOptions formattingOptions = new AppointmentFormattingOptions();

formattingOptions.setLocationFormat("Where: {0}");

formattingOptions.setTitleFormat("Subject: {0}");

formattingOptions.setDescriptionFormat("\r\n*~*~*~*~*~*~*~*~*~*\r\n{0}");

System.out.println(appointment.getAppointmentText(formattingOptions));

```
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)

{{% alert color="primary" %}} 

For more details, visit [Formatting an Appointment](/email/java/working-with-appointments/).

{{% /alert %}}
