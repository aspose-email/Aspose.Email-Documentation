---
title: "Trabalhando com Itens do Calendário do Outlook"
url: /pt/java/trabalhando-com-itens-do-calendario-do-outlook/
weight: 120
type: docs
---

## **Trabalhando com MapiCalendar**

A classe [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) da Aspose.Email fornece métodos e atributos para definir várias propriedades de um item de calendário. Este artigo fornece exemplos de código para:

- [**Trabalhando com MapiCalendar**](#trabalhando-com-mapicalendar)
  - [**Criando e Salvando Itens do Calendário**](#criando-e-salvando-itens-do-calendario)
  - [**Salvando o Item do Calendário como MSG**](#salvando-o-item-do-calendario-como-msg)
  - [**Adicionando Lembrete de Exibição a um Calendário**](#adicionando-lembrete-de-exibicao-a-um-calendario)
  - [**Adicionando Lembrete de Áudio a um Calendário**](#adicionando-lembrete-de-audio-a-um-calendario)
  - [**Adicionar/Recuperar Anexos de Arquivos de Calendário**](#adicionarrecuperar-anexos-de-arquivos-de-calendario)
  - [**Status dos Recipientes de um Pedido de Reunião**](#status-dos-recipientes-de-um-pedido-de-reuniao)
  - [**Criar MapiCalendarTimeZone a partir do Fuso Horário Padrão**](#criar-mapicalendartimezone-a-partir-do-fuso-horario-padrao)
- [**Definindo Lembrete com a Consulta Criada**](#definindo-lembrete-com-a-consulta-criada)
  - [**Definindo um Lembrete Adicionando Tags**](#definindo-um-lembrete-adicionando-tags)
- [**Converter EML de Consulta para MSG com Corpo HTML**](#converter-eml-de-consulta-para-msg-com-corpo-html)


### **Criando e Salvando Itens do Calendário**

O seguinte trecho de código mostra como criar e salvar um item de calendário no formato ICS.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

Calendar cal = Calendar.getInstance();
cal.set(2012, Calendar.OCTOBER, 2, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2012, Calendar.OCTOBER, 2, 14, 0, 0);
Date endDate = cal.getTime();

MapiCalendar calendar = new MapiCalendar("LAKE ARGYLE WA 6743", 
                                         "Consulta", 
                                         "Esta é uma reunião muito importante :)", 
                                         startDate, 
                                         endDate);

calendar.save(dataDir + "CalendarItem_out.ics", AppointmentSaveFormat.Ics);
~~~


### **Salvando o Item do Calendário como MSG**

O seguinte trecho de código mostra como salvar o item do calendário como MSG.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~


### **Definindo um ID de produto ao salvar um Item do Calendário como ICS**

A propriedade [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) da classe [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) é usada para salvar um item de calendário MAPI em um arquivo iCalendar (ICS) preservando as informações de data e hora originais, bem como um identificador de produto personalizado. A propriedade especifica o identificador para o produto que criou o objeto iCalendar.

O seguinte exemplo de código mostra como trabalhar com dados iCalendar (ICS) dentro de um objeto de calendário MAPI:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
```


### **Adicionando Lembrete de Exibição a um Calendário**

O seguinte trecho de código mostra como adicionar um lembrete de exibição a um calendário.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Participante"));
// Criar Consulta
Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizador"), 
                                  attendees);
MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar calendar = (MapiCalendar) mapi.toMapiMessageItem();

// Definir Propriedades do calendário
calendar.setReminderSet(true);
calendar.setReminderDelta(5); // 45 min antes do início do evento

String savedFile = (dataDir + "calendarWithDisplayReminder.ics");
calendar.save(savedFile, AppointmentSaveFormat.Ics);
~~~


### **Adicionando Lembrete de Áudio a um Calendário**

O seguinte trecho de código mostra como adicionar um lembrete de áudio a um calendário.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Participante"));

Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizador"), 
                                  attendees);

MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar cal = (MapiCalendar) mapi.toMapiMessageItem();

cal.setReminderSet(true);
cal.setReminderDelta(58); // 58 min antes do início do evento
cal.setReminderFileParameter(dataDir + "Alarm01.wav");

String savedFile = dataDir + "calendarWithAudioReminder_out.ics";
cal.save(savedFile, AppointmentSaveFormat.Ics);
~~~


### **Adicionar/Recuperar Anexos de Arquivos de Calendário**

O seguinte trecho de código mostra como adicionar/recuperar anexos de arquivos de calendário.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

String[] files = new String[3];
files[0] = "attachment_1.doc";
files[1] = "download.png";
files[2] = "Desert.jpg";

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Participante"));

Appointment app1 = new Appointment("Home", 
                                   startDate, 
                                   endDate, 
                                   new MailAddress("organizer@domain.com", "Organizador"), 
                                   attendees);
for (String file : files) {
    app1.getAttachments().addItem(new Attachment(dataDir + file));
}

app1.save(dataDir + "appWithAttachments_out.ics", AppointmentSaveFormat.Ics);

Appointment app2 = Appointment.load(dataDir + "appWithAttachments_out.ics");
System.out.println(app2.getAttachments().size());
for (Attachment att : app2.getAttachments())
    System.out.println(att.getName());
~~~


### **Status dos Recipientes de um Pedido de Reunião**

O seguinte trecho de código mostra como obter o status dos recipientes de um pedido de reunião.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~


### **Criar MapiCalendarTimeZone a partir do Fuso Horário Padrão**

O seguinte trecho de código mostra como criar [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) a partir do fuso horário padrão.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Eastern Standard Time");
~~~


## **Definindo Lembrete com a Consulta Criada**

Um lembrete pode ser adicionado quando uma consulta é criada. Esses alarmes podem ser ativados com base em diferentes critérios, como n minutos antes do início programado, repetir n vezes em n intervalos. Diferentes tags podem ser usadas para criar esses gatilhos no script contido entre BEGIN:VALARM e END:VALARM dentro de uma consulta. Existem várias variantes nas quais o lembrete pode ser definido em uma consulta.

### **Definindo um Lembrete Adicionando Tags**

O seguinte trecho de código mostra como definir um lembrete adicionando tags.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();
long MIN_MS = 60 * 1000;
long HR_MS = 60 * MIN_MS;
long DAY_MS = 24 * HR_MS;

String location = "Local da Reunião: Sala 5";
Date startDate = getDate(1997, 3, 18, 18, 30, 00);
Date endDate = getDate(1997, 3, 18, 19, 30, 00);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");
MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("bbb@bmail.com", "Primeiro participante"));

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

// Lembrete de áudio que soará em um horário preciso e
// Repetirá mais 4 vezes em intervalos de 15 minutos:
AppointmentReminder audioReminder = new AppointmentReminder();
audioReminder.setTrigger(new ReminderTrigger(getDate(1997, 3, 17, 13, 30, 0)));
audioReminder.setRepeat(4);
audioReminder.setDuration(new ReminderDuration(15 * MIN_MS));
audioReminder.setAction(ReminderAction.Audio);
ReminderAttachment attach = new ReminderAttachment(new URI("ftp://Host.com/pub/sounds/bell-01.aud"));
audioReminder.getAttachments().addItem(attach);
target.getReminders().addItem(audioReminder);


// Lembrete de exibição que será disparado 30 minutos antes do
// Início programado do evento com o qual está
// Associado e repetirá mais 2 vezes em intervalos de 15 minutos:
AppointmentReminder displayReminder = new AppointmentReminder();
ReminderDuration dur = new ReminderDuration(-30 * MIN_MS);
displayReminder.setTrigger(new ReminderTrigger(dur, ReminderRelated.Start));
displayReminder.setRepeat(2);
displayReminder.setDuration(new ReminderDuration(15 * MIN_MS));
displayReminder.setAction(ReminderAction.Display);
displayReminder.setDescription("Reunião de café da manhã com equipe executiva às 8:30 AM EST");
target.getReminders().addItem(displayReminder);

// Alarme de e-mail que será acionado 2 dias antes da
// Data/hora programada. Não repete. O e-mail tem um assunto, corpo e link de anexo.
AppointmentReminder emailReminder = new AppointmentReminder();
ReminderDuration dur1 = new ReminderDuration(-2 * DAY_MS);
emailReminder.setTrigger(new ReminderTrigger(dur1, ReminderRelated.Start));
ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");
emailReminder.getAttendees().addItem(attendee);
emailReminder.setAction(ReminderAction.Email);
emailReminder.setSummary("LEMBRETE: ENVIE A AGENDA PARA A REUNIÃO SEMANAL DA EQUIPE");
emailReminder.setDescription("Uma agenda preliminar precisa ser enviada aos participantes da reunião semanal dos gerentes (MGR-LIST). Anexo está um link para o modelo do documento para o arquivo da agenda.");
ReminderAttachment attach1 = new ReminderAttachment(new URI("http://Host.com/templates/agenda.doc"));
emailReminder.getAttachments().addItem(attach1);
target.getReminders().addItem(emailReminder);

// Alarme procedural que será acionado em uma data/hora precisa
// E repetirá mais 23 vezes em intervalos de uma hora. O alarme irá
// Invocar um arquivo de procedimento.
AppointmentReminder procReminder = new AppointmentReminder();
procReminder.setTrigger(new ReminderTrigger(getDate(1998, 1, 1, 5, 0, 0)));
procReminder.setRepeat(23);
procReminder.setDuration(new ReminderDuration(1 * DAY_MS));
procReminder.setAction(ReminderAction.Procedure);
ReminderAttachment attach2 = new ReminderAttachment(new URI("ftp://Host.com/novo-procs/felizano.exe"));
procReminder.getAttachments().addItem(attach2);
target.getReminders().addItem(procReminder);
target.save(dataDir + "savedFile_out.ics");
~~~


## **Converter EML de Consulta para MSG com Corpo HTML**

Desde a versão 19.3, a Aspose.Email oferece a capacidade de converter EML de Consulta para MSG enquanto mantém o corpo HTML da consulta. A Aspose.Email fornece uma propriedade [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) que tem um valor padrão de **true.** Quando o valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) é definido como **true**, o corpo da consulta é convertido para o formato RTF. Para manter o formato do corpo da consulta em formato HTML, defina o valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) como **false.**

O seguinte exemplo demonstra o uso da propriedade [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) para manter o formato do corpo da consulta em formato HTML.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MailMessage mailMessage = MailMessage.load(dataDir + "TestAppointment.eml");

MapiConversionOptions conversionOptions = new MapiConversionOptions();
conversionOptions.setFormat(OutlookMessageFormat.Unicode);

// valor padrão para ForcedRtfBodyForAppointment é true
conversionOptions.setForcedRtfBodyForAppointment(false);

MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, conversionOptions);

if (mapiMessage.getBodyType() == BodyContentType.Html) {
    System.out.println("Tipo de Corpo: Html");
} else if (mapiMessage.getBodyType() == BodyContentType.Rtf) {
    System.out.println("Tipo de Corpo: Rtf");
}

mapiMessage.save(dataDir + "TestAppointment_out.msg");
~~~