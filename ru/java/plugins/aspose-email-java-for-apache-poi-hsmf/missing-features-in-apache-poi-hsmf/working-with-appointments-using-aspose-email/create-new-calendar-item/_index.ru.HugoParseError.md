---
title: Создание нового элемента календаря
type: docs
weight: 10
url: /java/create-new-calendar-item/
---

## **Aspose.Email - Создание нового элемента календаря**
Класс [Aspose.Email.MapiCalendar](https://apireference.aspose.com/email/java/com.aspose.email/mapicalendar) предоставляет методы и атрибуты, которые устанавливают различные свойства элемента календаря.

**Java**

``` java

 MapiCalendar appointment = new MapiCalendar(

    "Lorem ipsum dolor sit amet.",

    "Appointment",

    "This is a very important meeting :)",

    new Date(2012, 10, 2, 13, 0, 0),

    new Date(2012, 10, 2, 14, 0, 0));

appointment.save(dataDir + "AsposeCalendarItem.ics", AppointmentSaveFormat.Ics);

```
## **Скачать исполняемый код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите [Работа с MapiCalendar](/email/java/working-with-mapicalendar/).

{{% /alert %}}