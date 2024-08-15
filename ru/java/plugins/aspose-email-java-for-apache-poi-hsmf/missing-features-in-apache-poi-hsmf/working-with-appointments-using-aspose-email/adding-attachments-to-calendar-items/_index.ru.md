---
title: "Добавление вложений к элементам календаря"
url: /ru/java/adding-attachments-to-calendar-items/
weight: 60
type: docs
---

## **Aspose.Email - добавление вложений к элементам календаря**
Aspose.Email предоставляет коллекцию вложений, которую можно использовать для добавления вложений, связанных с элементами календаря.

**Java**

``` java

 Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addItem(new MailAddress("attendee_address@domain.com", "Attendee"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Appointment Location", "Appointment Summary", "Appointment Description",

									startDate, endDate,

									new MailAddress("organizer_address@domain.com", "Organizer"), attendees, expected);

//Attach a file from disc to this appointment

File file = new File(dataDir + "AsposeXLS.xls");

FileInputStream fis = new FileInputStream(file);

Attachment att = new Attachment(fis, file.getName());

app.getAttachments().addItem(att);

fis.close();

String savedFile = dataDir + "AppWithAttachments.ics";

app.save(savedFile, AppointmentSaveFormat.Ics);

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Добавление и получение вложений из элементов календаря](/email/java/working-with-appointments/).

{{% /alert %}}
