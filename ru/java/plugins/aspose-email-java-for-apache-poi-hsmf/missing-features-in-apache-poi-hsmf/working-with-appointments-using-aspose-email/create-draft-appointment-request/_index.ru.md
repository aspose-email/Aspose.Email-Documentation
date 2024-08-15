---
title: "Создайте черновик запроса на встречу"
url: /ru/java/create-draft-appointment-request/
weight: 40
type: docs
---

## **Aspose.Email - создайте черновик запроса на встречу**
Может быть полезно создать запрос на встречу в черновом режиме, чтобы добавить основную информацию, а затем тот же черновик встречи можно было бы переслать другим пользователям, которые могут внести изменения. Aspose.Email для Java позволяет создавать и сохранять встречу в черновом режиме для последующего использования.

Чтобы сохранить встречу в черновом режиме, для свойства Method класса Appointment необходимо задать значение **Publish**.

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
## **Загрузить рабочий код**
Download **Создайте черновик запроса на встречу** с любого из нижеперечисленных сайтов социального кодирования:

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Создайте черновик запроса на встречу](/email/java/working-with-appointments/).

{{% /alert %}}
