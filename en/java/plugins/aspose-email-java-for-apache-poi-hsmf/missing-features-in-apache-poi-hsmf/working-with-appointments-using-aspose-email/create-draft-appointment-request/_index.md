---
title: Create Draft Appointment Request
type: docs
weight: 40
url: /java/create-draft-appointment-request/
---

## **Aspose.Email - Create Draft Appointment Request**
It can be useful to create an appointment request in draft mode, so that the basic information is added and then the same draft appointment can be forwarded to other users who might make changes. Aspose.Email for Java provides the flexibility to create and save an appointment in draft mode for later use.

In order to save an appointment in draft mode, the Method property of the Appointment class should be set to **Publish**.

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
## **Download Running Code**
Download **Create Draft Appointment Request** form any of the below mentioned social coding sites:

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)

{{% alert color="primary" %}} 

For more details, visit [Create a Draft Appointment Request](/email/java/working-with-appointments/).

{{% /alert %}}
