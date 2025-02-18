---
title: "Criar Novo Item de Calendário"
url: /pt/java/create-new-calendar-item/
weight: 10
type: docs
---

## **Aspose.Email - Criar Novo Item de Calendário**
A classe [MapiCalendar](https://apireference.aspose.com/email/java/com.aspose.email/mapicalendar) do Aspose.Email fornece métodos e atributos que definem várias propriedades de um item de calendário.

**Java**

``` java

 MapiCalendar appointment = new MapiCalendar(

    "Lorem ipsum dolor sit amet.",

    "Compromisso",

    "Esta é uma reunião muito importante :)",

    new Date(2012, 10, 2, 13, 0, 0),

    new Date(2012, 10, 2, 14, 0, 0));

appointment.save(dataDir + "AsposeCalendarItem.ics", AppointmentSaveFormat.Ics);

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/createcalenderitem/AsposeNewCalenderItems.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Trabahando com MapiCalendar](/email/java/working-with-mapicalendar/).

{{% /alert %}}