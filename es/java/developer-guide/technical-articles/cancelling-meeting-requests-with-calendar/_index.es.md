---
title: "Cancelando Solicitudes de Reunión con el Calendario"
url: /es/java/cancelando-solicitudes-de-reunion-con-el-calendario/
weight: 270
type: docs
---


Puede enviar una solicitud de cancelación de reunión con Aspose.Email utilizando el objeto de la clase Appointment. Necesita tener la información de la solicitud de reunión original para cancelar la solicitud. El ejemplo en este artículo primero envía una solicitud de reunión, guarda la información en una base de datos y luego cancela la solicitud basada en el ID del mensaje.
## **Enviando Solicitudes de Reunión**
Antes de poder [cancelar solicitudes de reunión](#cancelando-solicitudes-de-reunion), tenemos que enviar algunas:

1. Primero, cree una instancia del tipo SmtpClient para enviar el mensaje.
1. Guarde toda la información de los asistentes en la colección MailAddressCollection.
1. Cree una instancia de la clase MailMessage y las propiedades necesarias como From, To y Subject.
1. Cree una instancia del tipo Appointment y proporcione información sobre la ubicación, hora de inicio, hora de finalización, organizadores y asistentes.
1. Guarde toda la información en una base de datos. El trabajo relacionado con la base de datos se realiza en el método SaveIntoDB.

El siguiente fragmento de código le muestra cómo enviar solicitudes de reunión.



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
        // Crear una instancia de SMTPClient
        SmtpClient client = new SmtpClient("MailServer", "Username", "Password");
        // Obtener los asistentes
        MailAddressCollection attendees = new MailAddressCollection();
        for (Attendees a : attendeesArr) {
            attendees.addItem(new MailAddress(a.EmailAddress, a.DisplayName));
        }

        // Crear una instancia de MailMessage para enviar la invitación
        MailMessage msg = new MailMessage();

        // Establecer la dirección del remitente, asistentes
        msg.setFrom(new MailAddress(from));
        msg.setTo(attendees);

        // Crear una instancia de Appointment
        Appointment app = new Appointment(appLocation, appStartDate, appEndDate, new MailAddress(from), attendees);
        app.setSummary("Reunión Mensual");
        app.setDescription("Por favor, confirme su disponibilidad.");
        msg.addAlternateView(app.requestApointment());

        // Guardar la información en la base de datos
        if (saveIntoDB(msg, app) == true) {
            // Guardar el mensaje y enviar el mensaje con la solicitud de reunión
            msg.save(msg.getMessageId() + ".eml", SaveOptions.getDefaultEml());
            client.send(msg);
            System.out.println("mensaje enviado");
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

private boolean saveIntoDB(MailMessage msg, Appointment app) {
    // Guardar información del mensaje y de la cita
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

    // Guardar información de los asistentes
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
## **Cancelando Solicitud de Reunión**
Para cancelar una solicitud de reunión, primero obtenga el ID del mensaje del correo electrónico. Dado que hemos guardado esta información en una base de datos para este ejemplo, podemos recuperarla fácilmente.

1. Seleccionar el mensaje para el cual enviar la solicitud de cancelación.
1. Hacer clic en **Enviar Solicitud de Cancelación** para enviar la solicitud.
1. Consultar la base de datos para obtener la información de los asistentes, el mensaje y la relacionada con el calendario.
1. Crear instancias de las clases Calendar y MailMessage utilizando la información recuperada de la base de datos.
1. Utilizar el método Appointment.cancelAppointment() para enviar la solicitud de cancelación.
1. Enviar el correo utilizando SMTP.

El siguiente fragmento de código le muestra cómo cancelar la solicitud de reunión.



~~~Java
public void cancel(String messageId) {
    // Obtener la información del mensaje y del calendario de la base de datos obtener la información del asistente

    // Obtener la información del asistente en el lector
    Attendees[] attendeesRows = getAttendeesFromDB(messageId);

    // Crear una MailAddressCollection a partir de los asistentes encontrados en la base de datos
    MailAddressCollection attendees = new MailAddressCollection();
    for (Attendees attendeesRow : attendeesRows) {
        attendees.addItem(new MailAddress(attendeesRow.EmailAddress, attendeesRow.DisplayName));
    }
    // Obtener información del mensaje y del calendario
    Message messageRow = getMessageFromDB(messageId);

    // Crear el objeto Calendar a partir de la información de la base de datos
    Appointment app = new Appointment(messageRow.AppLocation, messageRow.AppSummary, messageRow.AppDescription, messageRow.AppStartDate, messageRow.AppEndDate,
            new MailAddress(messageRow.From), attendees);

    // Crear mensaje y establecer direcciones de origen y destino y añadir la solicitud de cancelación de reunión
    MailMessage msg = new MailMessage();
    msg.setFrom(new MailAddress(messageRow.From));
    msg.setTo(attendees);
    msg.setSubject("Cancelar reunión");
    msg.addAlternateView(app.cancelAppointment());
    SmtpClient smtp = new SmtpClient("smtp.gmail.com", 587, "user@gmail.com", "password");
    smtp.send(msg);
    System.out.println("solicitud de cancelación exitosa");
}
~~~