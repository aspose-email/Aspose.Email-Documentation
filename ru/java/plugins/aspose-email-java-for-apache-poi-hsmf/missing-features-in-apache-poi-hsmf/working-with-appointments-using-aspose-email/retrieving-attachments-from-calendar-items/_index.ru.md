---
title: "Извлечение вложений из элементов календаря"
url: /ru/java/retrieving-attachments-from-calendar-items/
weight: 70
type: docs
---

## **Aspose.Email - Извлечение вложений из элементов календаря**
Aspose.Email предоставляет коллекцию вложений, которая может быть использована для извлечения вложений, связанных с элементами календаря.

**Java**

``` java

 String savedFile = dataDir + "AppWithAttachments.ics";

Appointment app2 = Appointment.load(savedFile);

System.out.println("Всего вложений: "  + app2.getAttachments().size());

for (int i=0; i< app2.getAttachments().size();i++)

{

	Attachment att = app2.getAttachments().get_Item(i);

	System.out.println(att.getName());

	//Сохраните вложение на диск

	att.save(att.getName());

}

```
## **Скачать рабочий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать пример кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Добавление вложений из элементов календаря](/email/java/adding-attachments-to-calendar-items/).

{{% /alert %}}