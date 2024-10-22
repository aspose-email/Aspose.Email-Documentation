---
title: "Crear Nuevo Elemento del Calendario"
url: /es/java/crear-nuevo-elemento-del-calendario/
weight: 10
type: docs
---

## **Aspose.Email - Crear Nuevo Elemento del Calendario**
La clase [MapiCalendar](https://apireference.aspose.com/email/java/com.aspose.email/mapicalendar) de Aspose.Email proporciona métodos y atributos que establecen diversas propiedades de un elemento del calendario.

**Java**

``` java

 MapiCalendar appointment = new MapiCalendar(

    "Lorem ipsum dolor sit amet.",

    "Cita",

    "Esta es una reunión muy importante :)",

    new Date(2012, 10, 2, 13, 0, 0),

    new Date(2012, 10, 2, 14, 0, 0));

appointment.save(dataDir + "AsposeCalendarItem.ics", AppointmentSaveFormat.Ics);

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Ejemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Trabajando con MapiCalendar](/email/java/working-with-mapicalendar/).

{{% /alert %}}