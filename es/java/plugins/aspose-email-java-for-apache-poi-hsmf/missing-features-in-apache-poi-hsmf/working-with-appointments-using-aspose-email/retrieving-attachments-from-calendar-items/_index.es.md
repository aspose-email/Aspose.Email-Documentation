---
title: "Recuperar archivos adjuntos de elementos del calendario"
url: /es/java/retrieving-attachments-from-calendar-items/
weight: 70
type: docs
---

## **Aspose.Email: recuperación de archivos adjuntos de elementos del calendario**
Aspose.Email proporciona una colección de archivos adjuntos que se puede usar para recuperar los archivos adjuntos asociados a los elementos del calendario.

**Java**

``` java

 String savedFile = dataDir + "AppWithAttachments.ics";

Appointment app2 = Appointment.load(savedFile);

System.out.println("Total Attachments: "  + app2.getAttachments().size());

for (int i=0; i< app2.getAttachments().size();i++)

{

	Attachment att = app2.getAttachments().get_Item(i);

	System.out.println(att.getName());

	//Save the attachment to disc

	att.save(att.getName());

}

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Agregar archivos adjuntos desde elementos del calendario](/email/java/adding-attachments-to-calendar-items/).

{{% /alert %}}
