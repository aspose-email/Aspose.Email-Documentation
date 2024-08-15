---
title: "Отмена приглашений на собрания с помощью календаря"
url: /ru/java/cancelling-meeting-requests-with-calendar/
weight: 270
type: docs
---


Вы можете отправить запрос на отмену собрания с помощью Aspose.Email, используя объект Appointment Class. Чтобы отменить запрос, вам необходимо иметь исходную информацию о приглашении на собрание. В примере, приведенном в этой статье, сначала отправляется приглашение на собрание, информация сохраняется в базе данных, а затем отменяется запрос на основании идентификатора сообщения.
## **Отправка приглашений на собрание**
Прежде чем мы сможем [отменить приглашения на собрания](#cancelling-meeting-request), мы должны выслать некоторые из них:

1. Сначала создайте экземпляр типа SmtpClient для отправки сообщения.
1. Сохраните всю информацию об участниках в коллекции MailAddressCollection.
1. Создайте экземпляр класса MailMessage и необходимые свойства, такие как From, To и Subject.
1. Создайте экземпляр типа «Встреча» и укажите место, время начала и окончания, информацию об организаторах и участниках.
1. Сохраните всю информацию в базе данных. Работа, связанная с БД, выполняется с помощью метода SaveInToDB.

В следующем фрагменте кода показано, как отправлять приглашения на собрания.



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
## **Отмена приглашения на собрание**
Чтобы отменить приглашение на собрание, сначала получите идентификатор сообщения электронной почты. Поскольку для этого примера мы сохранили эту информацию в базе данных, мы можем легко получить ее снова.

1. Выбор сообщения, для которого нужно отправить запрос на отмену.
1. Click **Отправить запрос на отмену** для отправки запроса.
1. Запрашивает базу данных для получения информации об участнике, сообщении и календаре.
1. Создайте экземпляры классов Calendar Class и MailMessage, используя информацию, полученную из базы данных.
1. Используйте метод Appointment.cancelAppointment () для отправки запроса на отмену.
1. Отправьте письмо с помощью SMTP.

В следующем фрагменте кода показано, как отменить приглашение на собрание.



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
