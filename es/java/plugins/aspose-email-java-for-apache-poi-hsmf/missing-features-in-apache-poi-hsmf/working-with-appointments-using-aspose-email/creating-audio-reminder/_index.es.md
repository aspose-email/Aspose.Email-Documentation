---
title: "Creando Recordatorios de Audio"
url: /es/java/creando-recordatorios-de-audio/
weight: 50
type: docs
---

## **Aspose.Email - Creando Recordatorios de Audio**
Añadiendo un Recordatorio de Audio a un Calendario

**Java**

``` java

 Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addMailAddress(new MailAddress("attendee_address@domain.com", "Asistente"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Ubicación de la Cita", "Resumen de la Cita", "Descripción de la Cita",

									startDate, endDate,

									new MailAddress("organizer_address@domain.com", "Organizador"), attendees, expected);

MailMessage msg = new MailMessage();

msg.addAlternateView(app.requestApointment());

MapiMessage mapi = MapiMessage.fromMailMessage(msg);

MapiCalendar cal = (MapiCalendar)mapi.toMapiMessageItem();

cal.setRemainderSet(true);

cal.setRemainderDelta(58);//58 min antes del inicio del evento

cal.setReminderFileParameter("data/logon.wav");

cal.save("data/AsposeAudioReminder.ics", AppointmentSaveFormat.Ics);

```
## **Descargar Código en Ejecución**
Descarga **Creando Recordatorios de Audio** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [SourceForge](https://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Audio%20Reminders%20%28Aspose.Email%29.zip/download)
- [GitHub](https://sourceforge.net/projects/asposeforapachepoi/)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Audio%20Reminders%20\(Aspose.Email\).zip)

{{% alert color="primary" %}} 

Para más detalles, visita [Trabajando con MapiCalendar](/email/java/working-with-mapicalendar/).

{{% /alert %}}