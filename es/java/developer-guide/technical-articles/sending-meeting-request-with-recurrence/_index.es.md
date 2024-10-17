---
title: "Enviando solicitud de reunión con recurrencia"
url: /es/java/sending-meeting-request-with-recurrence/
weight: 240
type: docs
---


Con Aspose.Email, es posible generar una solicitud de reunión con recurrencia. Este artículo explica cómo se puede generar una solicitud de reunión con una recurrencia específica. El Id Único de la cita puede guardarse para su uso posterior para enviar cualquier actualización a la cita.
## **Generando Solicitud de Reunión con Recurrencia**
El siguiente ejemplo de código muestra cómo lograr esto.



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String szUniqueId;

// Crear un mensaje de correo
MailMessage msg1 = new MailMessage();
msg1.getTo().add("to@domain.com");
msg1.setFrom(new MailAddress("from@gmail.com"));

// Rellenar el objeto de cita
Date startDate = sdf.parse("2013-12-01 17:00:00");
Date endDate = sdf.parse("2013-12-31 17:30:00");

// Crear objeto de cita
Appointment agendaAppointment = new Appointment("same place", startDate, endDate, msg1.getFrom(), msg1.getTo());

// Crear id único ya que ayudará a acceder a esta cita más tarde
szUniqueId = UUID.randomUUID().toString();
agendaAppointment.setUniqueId(szUniqueId);
agendaAppointment.setDescription("----------------");

// Crear un objeto de patrón de recurrencia semanal
WeeklyRecurrencePattern pattern1 = new WeeklyRecurrencePattern(14);

// Establecer propiedades del patrón semanal como días: Lun, Mar y Jue
pattern1.setStartDays(new int[3]);
pattern1.getStartDays()[0] = CalendarDay.Monday;
pattern1.getStartDays()[1] = CalendarDay.Tuesday;
pattern1.getStartDays()[2] = CalendarDay.Thursday;
pattern1.setInterval(1);

// Establecer patrón de recurrencia para la cita
agendaAppointment.setRecurrence(pattern1);

// Adjuntar esta cita al correo
msg1.getAlternateViews().addItem(agendaAppointment.requestApointment());

// Crear SmtpClient
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
client.setSecurityOptions(SecurityOptions.Auto);

// Enviar correo con solicitud de cita
client.send(msg1);

// Devolver id único para uso posterior
// return szUniqueId;
~~~
## **Enviar Solicitud de Actualización de Cita**
Para enviar una actualización de la cita anterior, se requiere un id único. El siguiente código de ejemplo muestra cómo se puede enviar esta solicitud de actualización de cita



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
Date startDate = sdf.parse("2013-12-12 17:00:00");
Date endDate = sdf.parse("2013-12-12 17:30:00");
Appointment appUpdate = new Appointment("Different Place", startDate, endDate, new MailAddress("newcustomeronnet@gmail.com"),
        MailAddressCollection.to_MailAddressCollection("kashif.iqbal@aspose.com"));
appUpdate.setUniqueId(szUniqueId);
WeeklyRecurrencePattern pattern3 = (WeeklyRecurrencePattern) appUpdate.getRecurrence();
appUpdate.setSummary("actualizar resumen de solicitud de reunión");
appUpdate.setDescription("actualizar");
MailMessage msgUpdate = new MailMessage("newcustomeronnet@gmail.com", "kashif.iqbal@aspose.com", "06 - correo de prueba - actualizar solicitud de reunión", "correo de prueba");
msgUpdate.addAlternateView(appUpdate.updateAppointment());
SmtpClient smtp = new SmtpClient("server.domain.com", 587, "username", "password");
smtp.send(msgUpdate);
~~~