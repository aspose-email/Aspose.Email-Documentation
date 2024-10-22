---
title: "Crear Solicitud de Cita en Borrador"
url: /es/java/create-draft-appointment-request/
weight: 40
type: docs
---

## **Aspose.Email - Crear Solicitud de Cita en Borrador**
Puede ser útil crear una solicitud de cita en modo borrador, para que se agregue la información básica y luego la misma cita en borrador se pueda reenviar a otros usuarios que podrían hacer cambios. Aspose.Email para Java proporciona la flexibilidad para crear y guardar una cita en modo borrador para su uso posterior.

Para guardar una cita en modo borrador, la propiedad Method de la clase Appointment debe establecerse en **Publish**.

**Java**

``` java
 String sender = "test@gmail.com";

String recipient = "test@email.com";

MailMessage message = new MailMessage(sender, recipient, "", "");

Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addMailAddress(new MailAddress("attendee_address@aspose.com", "Attendee"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Appointment Location", "Appointment Summary", "Appointment Description",
        startDate, endDate,
        new MailAddress("organizer_address@aspose.com", "Organizer"), attendees, expected);

//Establecer la cita como borrador
app.setMethod(AppointmentMethodType.Publish);//.Method = AppointmentMethodType.Publish;

message.addAlternateView(app.requestApointment());

MapiMessage msg = MapiMessage.fromMailMessage(message);

// Guardar la cita como borrador.
msg.save("data/AsposeDraft.msg");
```
## **Descargar Código en Ejecución**
Descargue **Crear Solicitud de Cita en Borrador** de cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)

{{% alert color="primary" %}} 

Para más detalles, visite [Crear una Solicitud de Cita en Borrador](/email/java/working-with-appointments/).

{{% /alert %}}