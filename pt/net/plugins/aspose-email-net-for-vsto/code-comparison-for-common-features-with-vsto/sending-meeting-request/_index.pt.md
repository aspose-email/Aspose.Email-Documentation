---
title: "Enviando Solicitação de Reunião"
url: /pt/net/sending-meeting-request/
weight: 200
type: docs
---


## **VSTO**
Para usar classes do Outlook, o Outlook.Interop deve ser referenciado em seu projeto .NET. O código abaixo:

1. Cria uma solicitação de reunião.
1. Define propriedades como assunto, corpo, local e horário.
1. Envia a solicitação de reunião para o destinatário.
1. O Microsoft Outlook deve estar instalado no sistema onde este aplicativo de exemplo será executado.

``` cs

 // Cria uma instância da classe Outlook Application

Outlook.Application outlookApp = new Outlook.Application();

// Cria uma instância do objeto AppointmentItem e define as propriedades:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem)outlookApp.CreateItem(Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "assunto da reunião";

oAppointment.Body = "texto do corpo da reunião";

oAppointment.Location = "Local da reunião";

// Define as datas de início e fim

oAppointment.Start = Convert.ToDateTime("22/01/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("22/01/2010 2:00:00 PM");

// Salva a reunião

oAppointment.Save();

// Envia a reunião

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal();

mailItem.To = "destinatario@dominio.com";

mailItem.Send();

```
## **Aspose.Email**
O código abaixo usa Aspose.Email para .NET para enviar uma solicitação de reunião. Primeiro, crie a solicitação de reunião usando a classe Aspose.Email.Appointment. Em seguida, envie o e-mail, anexe a solicitação de reunião e envie o e-mail usando a classe Aspose.Email.Mail.SmtpClient.

Vantagens de usar Aspose.Email para .NET

Outlook Interop requer que o Microsoft Outlook esteja instalado no sistema onde é utilizado. Aspose.Email para .NET não requer a instalação do Microsoft Outlook e é adequado para aplicativos em servidor.

``` cs

  // Cria participantes da reunião

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("destinatario1@dominio.com");

attendees.Add("destinatario2@dominio.com");

// Configura a reunião

Appointment app = new Appointment(

    "Local", // local da reunião

    DateTime.Now, // data de início

    DateTime.Now.AddHours(1), // data de fim

    new MailAddress("organizador@dominio.com"), // organizador

    attendees); // participantes

// Configura a mensagem que precisa ser enviada

MailMessage msg = new MailMessage();

msg.From = "de@dominio.com";

msg.To = "para@dominio.com";

msg.Subject = "solicitação de reunião";

msg.Body = "você está convidado";

// Adiciona solicitação de reunião à mensagem

msg.AddAlternateView(app.RequestApointment());

// Configura o cliente SMTP para enviar e-mail com solicitação de reunião

SmtpClient client = new SmtpClient("host", 25 ,"usuario", "senha");

client.Send(msg);

```
##**Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772944)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Sending.Meeting.Request.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Sending%20Meeting%20Request%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Sending%20Meeting%20Request%20\(Aspose.Email\).zip)