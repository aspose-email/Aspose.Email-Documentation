---
title: "Добавление вложений к элементам календаря"
url: /ru/java/adding-attachments-to-calendar-items/
weight: 60
type: docs
---

## **Aspose.Email - Добавление вложений к элементам календаря**
Aspose.Email предоставляет коллекцию вложений, которую можно использовать для добавления вложений, связанных с элементами календаря.

**Java**

``` java

 Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addItem(new MailAddress("attendee_address@domain.com", "Участник"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Место встречи", "Сводка встречи", "Описание встречи",

									startDate, endDate,

									new MailAddress("organizer_address@domain.com", "Организатор"), attendees, expected);

//Прикрепить файл с диска к этой встрече

File file = new File(dataDir + "AsposeXLS.xls");

FileInputStream fis = new FileInputStream(file);

Attachment att = new Attachment(fis, file.getName());

app.getAttachments().addItem(att);

fis.close();

String savedFile = dataDir + "AppWithAttachments.ics";

app.save(savedFile, AppointmentSaveFormat.Ics);

```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите [Добавление и извлечение вложений из элементов календаря](/email/java/working-with-appointments/).

{{% /alert %}}