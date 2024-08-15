---
title: "Cómo formatear una cita en Aspose.Email"
url: /es/java/formatting-an-appointment-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Cómo formatear una cita**
La clase AppointmentFormattingOptions se puede usar para dar formato a la cita en formato de texto y HTML.

**Java**

``` java

 Appointment appointment = Appointment.load(dataDir + "appointment.ics");

AppointmentFormattingOptions formattingOptions = new AppointmentFormattingOptions();

formattingOptions.setLocationFormat("Where: {0}");

formattingOptions.setTitleFormat("Subject: {0}");

formattingOptions.setDescriptionFormat("\r\n*~*~*~*~*~*~*~*~*~*\r\n{0}");

System.out.println(appointment.getAppointmentText(formattingOptions));

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Formatear una cita](/email/java/working-with-appointments/).

{{% /alert %}}
