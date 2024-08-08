---
title: Retrieving Attachments from Calendar Items
type: docs
weight: 70
url: /java/retrieving-attachments-from-calendar-items/
---

## **Aspose.Email - Retrieving Attachments from Calendar Items**
Aspose.Email provides an attachments collection that can be used to retrieve attachments associated with calendar items.

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
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)

{{% alert color="primary" %}} 

For more details, visit [Adding Attachments from Calendar Items](/email/java/adding-attachments-to-calendar-items/).

{{% /alert %}}
