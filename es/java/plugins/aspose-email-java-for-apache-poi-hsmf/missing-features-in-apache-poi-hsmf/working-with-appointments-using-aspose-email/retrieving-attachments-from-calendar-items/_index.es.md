---
title: "Recuperando Adjuntos de Elementos de Calendario"
url: /es/java/retrieving-attachments-from-calendar-items/
weight: 70
type: docs
---

## **Aspose.Email - Recuperando Adjuntos de Elementos de Calendario**
Aspose.Email proporciona una colección de adjuntos que se puede utilizar para recuperar adjuntos asociados con elementos de calendario.

**Java**

``` java

 String savedFile = dataDir + "AppWithAttachments.ics";

Appointment app2 = Appointment.load(savedFile);

System.out.println("Total Adjuntos: "  + app2.getAttachments().size());

for (int i=0; i< app2.getAttachments().size();i++)

{

	Attachment att = app2.getAttachments().get_Item(i);

	System.out.println(att.getName());

	//Guardar el adjunto en disco

	att.save(att.getName());

}

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Añadiendo Adjuntos de Elementos de Calendario](/email/java/adding-attachments-to-calendar-items/).

{{% /alert %}}