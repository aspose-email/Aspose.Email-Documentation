---
title: Cancelling Meeting Requests with Calendar
type: docs
weight: 270
url: /java/cancelling-meeting-requests-with-calendar/
---


You can send a meeting cancellation request with Aspose.Email using the Appointment Class object. You need to have the original meeting request information to cancel the request. The example in this article first sends a meeting request, saves the information in a database and then cancels the request based of the message ID.
## **Sending Meeting Requests**
Before we can [cancel meeting requests](#cancelling-meeting-request), we have to send some out:

1. First create an instance of type SmtpClient for sending the message.
1. Save all the attendee information in the MailAddressCollection collection.
1. Create an instance of the MailMessage class and necessary properties like From, To and Subject.
1. Create an instance of type Appointment and give location, start time, end time, organizers and attendees information.
1. Save all the information in an database. DB related work is being done in the SaveIntoDB method.

The following code snippet shows you how to send meeting requests.



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
## **Cancelling Meeting Request**
To cancel a meeting request, first get the email message's message ID. Since we have saved this information in a database for this example, we can easily get it again.

1. Selecting the message for which to send the cancellation request.
1. Click **Send Cancel Request** to send the request.
1. Queries the database to get the attendee, message and calendar related information.
1. Create an instances of the Calendar Class and MailMessage class classes using the information retrieved from the database.
1. Use the Appointment.cancelAppointment() method to send the cancellation request.
1. Send the mail using the SMTP.

The following code snippet shows you how to cancel the meeting request.



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
