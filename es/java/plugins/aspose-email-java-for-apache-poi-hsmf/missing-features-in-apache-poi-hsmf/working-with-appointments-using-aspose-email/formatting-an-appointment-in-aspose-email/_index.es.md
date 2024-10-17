---
title: "Formatear una Cita en Aspose.Email"
url: /es/java/formatear-una-cita-en-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Formatear una Cita**
La clase AppointmentFormattingOptions se puede usar para formatear la cita en formato de texto y HTML.

**Java**

``` java

 Appointment appointment = Appointment.load(dataDir + "appointment.ics");

AppointmentFormattingOptions formattingOptions = new AppointmentFormattingOptions();

formattingOptions.setLocationFormat("Dónde: {0}");

formattingOptions.setTitleFormat("Asunto: {0}");

formattingOptions.setDescriptionFormat("\r\n*~*~*~*~*~*~*~*~*~*\r\n{0}");

System.out.println(appointment.getAppointmentText(formattingOptions));

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Formatear una Cita](/email/java/working-with-appointments/).

{{% /alert %}}