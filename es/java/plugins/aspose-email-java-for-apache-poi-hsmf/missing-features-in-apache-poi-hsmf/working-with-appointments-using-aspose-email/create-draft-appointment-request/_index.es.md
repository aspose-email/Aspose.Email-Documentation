---
title: "Crear borrador de solicitud de cita"
url: /es/java/create-draft-appointment-request/
weight: 40
type: docs
---

## **Aspose.Email - Crear borrador de solicitud de cita**
Puede resultar útil crear una solicitud de cita en modo borrador, de modo que se añada la información básica y, a continuación, el mismo borrador de cita se pueda reenviar a otros usuarios que puedan realizar cambios. Aspose.Email para Java ofrece la flexibilidad de crear y guardar una cita en modo borrador para usarla más adelante.

Para guardar una cita en modo borrador, la propiedad Method de la clase Appointment debe configurarse en **Publish**.

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

//Set the Appointment as Draft

app.setMethod(AppointmentMethodType.Publish);//.Method = AppointmentMethodType.Publish;

message.addAlternateView(app.requestApointment());

MapiMessage msg = MapiMessage.fromMailMessage(message);

// Save the appointment as draft.

msg.save("data/AsposeDraft.msg");

```
## **Descargar Running Code**
Download **Crear borrador de solicitud de cita** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)

{{% alert color="primary" %}}

Para obtener más información, visite [Crear un borrador de solicitud de cita](/email/java/working-with-appointments/).

{{% /alert %}}
