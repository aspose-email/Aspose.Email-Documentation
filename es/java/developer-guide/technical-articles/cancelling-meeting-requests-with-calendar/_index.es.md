---
title: "Cancelación de convocatorias de reunión con calendario"
url: /es/java/cancelling-meeting-requests-with-calendar/
weight: 270
type: docs
---


Puede enviar una solicitud de cancelación de reunión con Aspose.Email mediante el objeto Appointment Class. Debe tener la información original de la solicitud de reunión para cancelar la solicitud. En el ejemplo de este artículo, primero se envía una convocatoria de reunión, se guarda la información en una base de datos y, a continuación, se cancela la convocatoria en función del identificador del mensaje.
## **Envío de convocatorias de reunión**
Antes de que podamos [cancelar convocatorias de reunión](#cancelling-meeting-request), tenemos que enviar algunos:

1. En primer lugar, cree una instancia de tipo SMTPClient para enviar el mensaje.
1. Guarda toda la información de los asistentes en la colección MailAddressCollection.
1. Crea una instancia de la clase MailMessage y las propiedades necesarias, como From, To y Subject.
1. Cree una instancia de tipo Cita e indique la ubicación, la hora de inicio, la hora de finalización, los organizadores y los asistentes.
1. Guarda toda la información en una base de datos. El trabajo relacionado con la base de datos se está realizando con el método SaveIntoDB.

El siguiente fragmento de código muestra cómo enviar convocatorias de reunión.



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
## **Cancelación de la solicitud de reunión**
Para cancelar una convocatoria de reunión, primero obtenga el ID de mensaje del mensaje de correo electrónico. Como hemos guardado esta información en una base de datos para este ejemplo, podemos volver a obtenerla fácilmente.

1. Seleccionar el mensaje para el que enviar la solicitud de cancelación.
1. Click **Enviar solicitud de cancelación** para enviar la solicitud.
1. Consulta la base de datos para obtener información relacionada con los asistentes, los mensajes y el calendario.
1. Cree instancias de las clases Calendar Class y MailMessage con la información recuperada de la base de datos.
1. Utilice el método Appointment.cancelAppointment () para enviar la solicitud de cancelación.
1. Envía el correo mediante el SMTP.

El siguiente fragmento de código muestra cómo cancelar la convocatoria de reunión.



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
