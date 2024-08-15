---
title: "Crear nuevo elemento de calendario"
url: /es/java/create-new-calendar-item/
weight: 10
type: docs
---

## **Aspose.Email - Crear un nuevo elemento de calendario**
Aspose.Email's [MapiCalendar](https://apireference.aspose.com/email/java/com.aspose.email/mapicalendar) La clase proporciona métodos y atributos que establecen varias propiedades de un elemento del calendario.

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
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Trabajando con MapiCalendar](/email/java/working-with-mapicalendar/).

{{% /alert %}}
