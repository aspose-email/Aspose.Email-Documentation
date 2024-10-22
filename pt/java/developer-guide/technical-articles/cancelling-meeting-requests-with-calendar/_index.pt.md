---
title: "Cancelando Solicitações de Reunião com o Calendário"
url: /pt/java/cancelando-solicitacoes-de-reuniao-com-calendario/
weight: 270
type: docs
---


Você pode enviar uma solicitação de cancelamento de reunião com Aspose.Email usando o objeto da classe Appointment. Você precisa ter as informações da solicitação de reunião original para cancelar a solicitação. O exemplo neste artigo envia primeiro uma solicitação de reunião, salva as informações em um banco de dados e, em seguida, cancela a solicitação com base na ID da mensagem.
## **Enviando Solicitações de Reunião**
Antes que possamos [cancelar solicitações de reunião](#cancelando-solicitacoes-de-reuniao), precisamos enviar algumas:

1. Primeiro, crie uma instância do tipo SmtpClient para enviar a mensagem.
1. Salve todas as informações dos participantes na coleção MailAddressCollection.
1. Crie uma instância da classe MailMessage e das propriedades necessárias, como From, To e Subject.
1. Crie uma instância do tipo Appointment e forneça a localização, hora de início, hora de término, organizadores e informações dos participantes.
1. Salve todas as informações em um banco de dados. O trabalho relacionado ao DB está sendo realizado no método SaveIntoDB.

O seguinte trecho de código mostra como enviar solicitações de reunião.



~~~Java
class Attendees {
    public String MessageId;
    public String EmailAddress;
    public String DisplayName;
}

class Message {
    public String MessageId;
    public String From;
    public String Subject;
    public String Body;
    public String AppLocation;
    public Date AppStartDate;
    public Date AppEndDate;
    public String AppSummary;
    public String AppDescription;
}

public void send(Attendees[] attendeesArr, String from, String appLocation, Date appStartDate, Date appEndDate) {
    try {
        // Create an instance of SMTPClient
        SmtpClient client = new SmtpClient("MailServer", "Username", "Password");
        // Get the attendees
        MailAddressCollection attendees = new MailAddressCollection();
        for (Attendees a : attendeesArr) {
            attendees.addItem(new MailAddress(a.EmailAddress, a.DisplayName));
        }

        // Create an instance of MailMessage for sending the invitation
        MailMessage msg = new MailMessage();

        // Set from address, attendees
        msg.setFrom(new MailAddress(from));
        msg.setTo(attendees);

        // Create am instance of Appointment
        Appointment app = new Appointment(appLocation, appStartDate, appEndDate, new MailAddress(from), attendees);
        app.setSummary("Monthly Meeting");
        app.setDescription("Please confirm your availability.");
        msg.addAlternateView(app.requestApointment());

        // Save the info to the database
        if (saveIntoDB(msg, app) == true) {
            // Save the message and Send the message with the meeting request
            msg.save(msg.getMessageId() + ".eml", SaveOptions.getDefaultEml());
            client.send(msg);
            System.out.println("message sent");
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

private boolean saveIntoDB(MailMessage msg, Appointment app) {
    // Save Message and Appointment information
    Message messageRow = new Message();
    messageRow.MessageId = msg.getMessageId();
    messageRow.From = msg.getFrom().getAddress();
    messageRow.Subject = msg.getSubject();
    messageRow.Body = msg.getBody();
    messageRow.AppLocation = app.getLocation();
    messageRow.AppStartDate = app.getStartDate();
    messageRow.AppEndDate = app.getEndDate();
    messageRow.AppSummary = app.getSummary();
    messageRow.AppDescription = app.getDescription();
    addToDB(messageRow);

    // Save attendee information
    for (MailAddress address : app.getAttendees()) {
        Attendees attendeesRow = new Attendees();
        attendeesRow.MessageId = msg.getMessageId();
        attendeesRow.EmailAddress = address.getAddress();
        attendeesRow.DisplayName = address.getDisplayName();
        addToDB(attendeesRow);
    }

    return true;
}
~~~
## **Cancelando Solicitação de Reunião**
Para cancelar uma solicitação de reunião, primeiro obtenha a ID da mensagem do email. Como salvamos esta informação em um banco de dados para este exemplo, podemos facilmente recuperá-la novamente.

1. Selecionar a mensagem para a qual enviar a solicitação de cancelamento.
1. Clique em **Enviar Solicitação de Cancelamento** para enviar a solicitação.
1. Consulta o banco de dados para obter as informações relacionadas aos participantes, mensagem e calendário.
1. Crie instâncias das classes Calendar e MailMessage usando as informações recuperadas do banco de dados.
1. Use o método Appointment.cancelAppointment() para enviar a solicitação de cancelamento.
1. Envie o email usando o SMTP.

O seguinte trecho de código mostra como cancelar a solicitação de reunião.



~~~Java
public void cancel(String messageId) {
    // Get the message and calendar information from the database get the attendee information

    // Get the attendee information in reader
    Attendees[] attendeesRows = getAttendeesFromDB(messageId);

    // Create a MailAddressCollection from the attendees found in the database
    MailAddressCollection attendees = new MailAddressCollection();
    for (Attendees attendeesRow : attendeesRows) {
        attendees.addItem(new MailAddress(attendeesRow.EmailAddress, attendeesRow.DisplayName));
    }
    // Get message and calendar information
    Message messageRow = getMessageFromDB(messageId);

    // Create the Calendar object from the database information
    Appointment app = new Appointment(messageRow.AppLocation, messageRow.AppSummary, messageRow.AppDescription, messageRow.AppStartDate, messageRow.AppEndDate,
            new MailAddress(messageRow.From), attendees);

    // Create message and Set from and to addresses and Add the cancel meeting request
    MailMessage msg = new MailMessage();
    msg.setFrom(new MailAddress(messageRow.From));
    msg.setTo(attendees);
    msg.setSubject("Cencel meeting");
    msg.addAlternateView(app.cancelAppointment());
    SmtpClient smtp = new SmtpClient("smtp.gmail.com", 587, "user@gmail.com", "password");
    smtp.send(msg);
    System.out.println("cancellation request successfull");
}
~~~