---
title: "Создание черновика запроса на назначение"
url: /ru/java/create-draft-appointment-request/
weight: 40
type: docs
---

## **Aspose.Email - Создание черновика запроса на назначение**
Создание запроса на назначение в черновом режиме может быть полезным, чтобы добавить основную информацию, а затем этот же черновик можно переслать другим пользователям, которые могут внести изменения. Aspose.Email для Java предоставляет гибкость для создания и сохранения назначения в черновом режиме для последующего использования.

Чтобы сохранить назначение в черновом режиме, свойство Method класса Appointment должно быть установлено на **Publish**.

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

attendees.addMailAddress(new MailAddress("attendee_address@aspose.com", "Участник"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Место проведения встречи", "Сводка назначения", "Описание назначения",

        startDate, endDate,

        new MailAddress("organizer_address@aspose.com", "Организатор"), attendees, expected);

//Установить назначение как черновик

app.setMethod(AppointmentMethodType.Publish);//.Method = AppointmentMethodType.Publish;

message.addAlternateView(app.requestApointment());

MapiMessage msg = MapiMessage.fromMailMessage(message);

// Сохранить назначение как черновик.

msg.save("data/AsposeDraft.msg");

```
## **Скачать рабочий код**
Скачайте **Создание черновика запроса на назначение** с любого из упомянутых ниже сайтов социального кодирования:

- [CodePlex](https://asposeapachepoi.codeplex.com/downloads/get/1381615)
- [SourceForge](http://sourceforge.net/projects/asposeforapachepoi/files/Aspose.Email%20Features%20Not%20in%20Apache%20POI%20HSMF%20for%20Outlook/Create%20Draft%20Appointment%20Request%20%28Aspose.Email%29.zip/download)
- [GitHub](https://github.com/asposemarketplace/Aspose_for_Apache_POI/releases/download/More-Features-in-Aspose.Email-v1.1/Create.Draft.Appointment.Request.Aspose.Email.zip)
- [BitBucket](https://bitbucket.org/asposemarketplace/aspose-for-apache-poi/downloads/Create%20Draft%20Appointment%20Request%20\(Aspose.Email\).zip)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите [Создание запроса на черновик назначения](/email/java/working-with-appointments/).

{{% /alert %}}