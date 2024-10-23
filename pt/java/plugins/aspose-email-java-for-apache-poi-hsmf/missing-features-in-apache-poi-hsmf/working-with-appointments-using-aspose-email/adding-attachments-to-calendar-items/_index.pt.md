---
title: "Adicionando Anexos a Itens do Calendário"
url: /pt/java/adding-attachments-to-calendar-items/
weight: 60
type: docs
---

## **Aspose.Email - Adicionando Anexos a Itens do Calendário**
Aspose.Email fornece uma coleção de anexos que pode ser usada para adicionar anexos associados a itens do calendário.

**Java**

``` java

 Calendar calendar = Calendar.getInstance(TimeZone.getTimeZone("GMT"));

calendar.set(2012, Calendar.NOVEMBER, 1, 0, 0, 0);

Date startDate = calendar.getTime();

calendar.set(2012, Calendar.DECEMBER, 1);

Date endDate = calendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();

attendees.addItem(new MailAddress("attendee_address@domain.com", "Participante"));

WeeklyRecurrencePattern expected = new WeeklyRecurrencePattern(3);

Appointment app = new Appointment("Localização do Compromisso", "Resumo do Compromisso", "Descrição do Compromisso",

									startDate, endDate,

									new MailAddress("organizer_address@domain.com", "Organizador"), attendees, expected);

//Anexar um arquivo do disco a este compromisso

File file = new File(dataDir + "AsposeXLS.xls");

FileInputStream fis = new FileInputStream(file);

Attachment att = new Attachment(fis, file.getName());

app.getAttachments().addItem(att);

fis.close();

String savedFile = dataDir + "AppComAnexos.ics";

app.save(savedFile, AppointmentSaveFormat.Ics);

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/addattachmentstocalenderitems/AsposeAddAttachmentToCalenderItems.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Adicionando e Recuperando Anexos de Itens do Calendário](/email/java/working-with-appointments/).

{{% /alert %}}