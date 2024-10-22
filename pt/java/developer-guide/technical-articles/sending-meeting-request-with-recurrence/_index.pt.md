---
title: "Enviando solicitação de reunião com recorrência"
url: /pt/java/enviando-solicitacao-de-reuniao-com-recorrencia/
weight: 240
type: docs
---


Com Aspose.Email, é possível gerar uma solicitação de reunião com recorrência. Este artigo explica como uma solicitação de reunião pode ser gerada com uma recorrência específica. O Id Único do Compromisso pode ser salvo para uso futuro ao enviar qualquer atualização para o compromisso.
## **Gerando Solicitação de Reunião com Recorrência**
O seguinte exemplo de código mostra como alcançar isso.



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String szUniqueId;

// Criar uma mensagem de e-mail
MailMessage msg1 = new MailMessage();
msg1.getTo().add("to@domain.com");
msg1.setFrom(new MailAddress("from@gmail.com"));

// Preencher o objeto compromisso
Date startDate = sdf.parse("2013-12-01 17:00:00");
Date endDate = sdf.parse("2013-12-31 17:30:00");

// Criar objeto compromisso
Appointment agendaAppointment = new Appointment("mesmo lugar", startDate, endDate, msg1.getFrom(), msg1.getTo());

// Criar id único, pois ajudará a acessar este compromisso mais tarde
szUniqueId = UUID.randomUUID().toString();
agendaAppointment.setUniqueId(szUniqueId);
agendaAppointment.setDescription("----------------");

// Criar um objeto padrão de recorrência semanal
WeeklyRecurrencePattern pattern1 = new WeeklyRecurrencePattern(14);

// Definir propriedades do padrão semanal como dias: Seg, Ter e Qui
pattern1.setStartDays(new int[3]);
pattern1.getStartDays()[0] = CalendarDay.Monday;
pattern1.getStartDays()[1] = CalendarDay.Tuesday;
pattern1.getStartDays()[2] = CalendarDay.Thursday;
pattern1.setInterval(1);

// Definir padrão de recorrência para o compromisso
agendaAppointment.setRecurrence(pattern1);

// Anexar este compromisso ao e-mail
msg1.getAlternateViews().addItem(agendaAppointment.requestApointment());

// Criar SmtpClient
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
client.setSecurityOptions(SecurityOptions.Auto);

// Enviar e-mail com solicitação de compromisso
client.send(msg1);

// Retornar id único para uso futuro
// return szUniqueId;
~~~
## **Enviar Solicitação de Atualização de Compromisso**
Para enviar uma atualização para o compromisso anterior, o id único é necessário. O seguinte exemplo de código mostra como esta solicitação de atualização de compromisso pode ser enviada.



~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
Date startDate = sdf.parse("2013-12-12 17:00:00");
Date endDate = sdf.parse("2013-12-12 17:30:00");
Appointment appUpdate = new Appointment("Lugar Diferente", startDate, endDate, new MailAddress("newcustomeronnet@gmail.com"),
        MailAddressCollection.to_MailAddressCollection("kashif.iqbal@aspose.com"));
appUpdate.setUniqueId(szUniqueId);
WeeklyRecurrencePattern pattern3 = (WeeklyRecurrencePattern) appUpdate.getRecurrence();
appUpdate.setSummary("atualizar resumo da solicitação de reunião");
appUpdate.setDescription("atualização");
MailMessage msgUpdate = new MailMessage("newcustomeronnet@gmail.com", "kashif.iqbal@aspose.com", "06 - e-mail de teste - atualizar solicitação de reunião", "e-mail de teste");
msgUpdate.addAlternateView(appUpdate.updateAppointment());
SmtpClient smtp = new SmtpClient("server.domain.com", 587, "username", "password");
smtp.send(msgUpdate);
~~~