---
title: "Agregar Adjuntos a Elementos de Calendario"
url: /es/java/adding-attachments-to-calendar-items/
weight: 60
type: docs
---

## **Aspose.Email - Agregar Adjuntos a Elementos de Calendario**
Aspose.Email proporciona una colección de adjuntos que se puede utilizar para agregar adjuntos asociados con elementos de calendario.

**Java**

``` java

 Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addItem(new MailAddress("attendee_address@domain.com", "Asistente"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Ubicación de la Cita", "Resumen de la Cita", "Descripción de la Cita",

									startDate, endDate,

									new MailAddress("organizer_address@domain.com", "Organizador"), attendees, expected);

//Adjuntar un archivo del disco a esta cita

File file = new File(dataDir + "AsposeXLS.xls");

FileInputStream fis = new FileInputStream(file);

Attachment att = new Attachment(fis, file.getName());

app.getAttachments().addItem(att);

fis.close();

String savedFile = dataDir + "AppWithAttachments.ics";

app.save(savedFile, AppointmentSaveFormat.Ics);

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Agregar y Recuperar Adjuntos de Elementos de Calendario](/email/java/working-with-appointments/).

{{% /alert %}}