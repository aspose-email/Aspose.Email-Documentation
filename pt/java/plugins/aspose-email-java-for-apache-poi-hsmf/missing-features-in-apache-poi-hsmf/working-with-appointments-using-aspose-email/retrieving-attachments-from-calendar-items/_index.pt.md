---
title: "Recuperando Anexos de Itens de Calendário"
url: /pt/java/retrieving-attachments-from-calendar-items/
weight: 70
type: docs
---

## **Aspose.Email - Recuperando Anexos de Itens de Calendário**
Aspose.Email fornece uma coleção de anexos que pode ser usada para recuperar anexos associados a itens de calendário.

**Java**

``` java

 String savedFile = dataDir + "AppWithAttachments.ics";

Appointment app2 = Appointment.load(savedFile);

System.out.println("Total de Anexos: "  + app2.getAttachments().size());

for (int i=0; i< app2.getAttachments().size();i++)

{

	Attachment att = app2.getAttachments().get_Item(i);

	System.out.println(att.getName());

	//Salvar o anexo no disco

	att.save(att.getName());

}

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/getattachmentsfromcalender/AsposeGetAttachmentsFromCalender.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Adicionando Anexos de Itens de Calendário](/email/java/adding-attachments-to-calendar-items/).

{{% /alert %}}