---
title: "Форматирование встречи в Aspose.Email"
url: /ru/java/formatting-an-appointment-in-aspose-email/
weight: 20
type: docs
---

## **Aspose.Email - Форматирование встречи**
Класс AppointmentFormattingOptions можно использовать для форматирования встречи в текстовом формате и формате HTML.

**Java**

``` java

 Appointment appointment = Appointment.load(dataDir + "appointment.ics");

AppointmentFormattingOptions formattingOptions = new AppointmentFormattingOptions();

formattingOptions.setLocationFormat("Where: {0}");

formattingOptions.setTitleFormat("Subject: {0}");

formattingOptions.setDescriptionFormat("\r\n*~*~*~*~*~*~*~*~*~*\r\n{0}");

System.out.println(appointment.getAppointmentText(formattingOptions));

```
## **Загрузить рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Загрузить образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/formattingappointment/AsposeFormatAppointments.java)

{{% alert color="primary" %}}

Для получения дополнительной информации посетите [Форматирование встречи](/email/java/working-with-appointments/).

{{% /alert %}}
