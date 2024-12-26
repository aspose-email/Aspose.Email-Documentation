---
title: Adding Attachments to Calendar Items
ArticleTitle: Adding Attachments to Calendar Items
type: docs
weight: 60
url: /java/adding-attachments-to-calendar-items/
---

## **Aspose.Email - Adding Attachments to Calendar Items**
Aspose.Email provides an attachments collection that can be used to add attachments associated with calendar items.

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
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)

{{% alert color="primary" %}} 

For more details, visit [Adding and Retrieving Attachments from Calendar Items](/email/java/working-with-appointments/).

{{% /alert %}}
