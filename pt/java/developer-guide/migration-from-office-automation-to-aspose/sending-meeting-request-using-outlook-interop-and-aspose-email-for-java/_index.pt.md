---
title: "Enviando Solicitação de Reunião Usando Outlook Interop e Aspose.Email para Java"
url: /pt/java/enviando-solicitacao-de-reuniao-usando-outlook-interop-e-aspose-email-para-java/
weight: 40
type: docs
---


{{% alert color="primary" %}} 

Nossas dicas de migração mostram como os produtos Aspose podem ser usados para melhorar suas aplicações e libertá-lo da dependência de automação tradicional.

Esta dica de migração envia uma solicitação de reunião a um destinatário. Ela demonstra como enviar uma solicitação de reunião de duas maneiras:

- [Usando Outlook Interop](#enviando-solicitacao-de-reuniao-com-outlook-interop).
- [Usando Aspose.Email para Java](#vantagens-de-usar-asposeemail-para-java).

 também discutiremos as vantagens da última abordagem.

{{% /alert %}} 
## **Enviando Solicitação de Reunião com Outlook Interop**
Para usar as classes do Outlook, o Outlook.Interop deve ser referenciado em seu projeto .NET. O trecho de código abaixo:

1. Cria uma solicitação de reunião.
1. Define propriedades como assunto, corpo, localização e hora.
1. Envia a solicitação de reunião ao destinatário.

Microsoft Outlook deve estar instalado no sistema onde este aplicativo de exemplo será executado.
### **Exemplos de Programação**
**C#**

~~~cs

// Crie uma instância da classe Outlook Application

Outlook.Application outlookApp = new Outlook.Application ();

// Crie uma instância do objeto AppointmentItem e defina as propriedades:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem) outlookApp.CreateItem (Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "assunto da reunião";

oAppointment.Body = "texto do corpo da reunião";

oAppointment.Location = "Localização da reunião";

// Defina a data de início e a data de término

oAppointment.Start = Convert.ToDateTime ("22/01/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("22/01/2010 2:00:00 PM");

// Salve a reunião

oAppointment.Save ();

// Envie a reunião

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal ();

mailItem.To = "destinatario@dominio.com";

mailItem.Send();


~~~
## **Enviando Solicitação de Reunião usando Aspose.Email para Java**
O código abaixo usa Aspose.Email para Java para enviar uma solicitação de reunião. Primeiro, crie a solicitação de reunião usando a classe [Aspose.Email Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment). Em seguida, envie o email, anexe a solicitação de reunião e envie o email usando a classe [Aspose.Email SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient).
### **Vantagens de usar Aspose.Email para Java**
Outlook Interop requer que o Microsoft Outlook esteja instalado no sistema onde é utilizado. Aspose.Email para Java não requer que o Microsoft Outlook esteja instalado e é adequado para aplicações de servidor.
### **Exemplos de Programação**

~~~Java

// Crie os participantes da reunião
MailAddressCollection attendees = new MailAddressCollection();
attendees.add("destinatario1@dominio.com");
attendees.add("destinatario2@dominio.com");

java.util.Calendar c = java.util.Calendar.getInstance();
Date startDate = c.getTime();
c.add(java.util.Calendar.HOUR_OF_DAY, 1);
Date endDate = c.getTime();

// Configure a reunião
Appointment app = new Appointment(
    "Localização", // localização da reunião
    startDate, // data de início
    endDate, // data de término
    new MailAddress("organizador@dominio.com"), // organizador
    attendees); // participantes

// Configure a mensagem que precisa ser enviada
MailMessage msg = new MailMessage();
msg.setFrom(new MailAddress("de@dominio.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("para@dominio.com"));
msg.setSubject("solicitação de reunião");
msg.setBody("você está convidado");

// Adicione a solicitação de reunião à mensagem
msg.addAlternateView(app.requestApointment());

// Configure o cliente SMTP para enviar email com a solicitação de reunião
try (SmtpClient client = new SmtpClient("host", 25, "user", "password")) {
    client.send(msg);
}

~~~