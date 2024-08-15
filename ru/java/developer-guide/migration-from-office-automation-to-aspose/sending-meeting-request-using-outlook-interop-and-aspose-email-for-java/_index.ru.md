---
title: "Отправка приглашения на собрание с помощью Outlook Interop и Aspose.Email для Java"
url: /ru/java/sending-meeting-request-using-outlook-interop-and-aspose-email-for-java/
weight: 40
type: docs
---


{{% alert color="primary" %}}

Наши советы по миграции показывают, как продукты Aspose можно использовать для улучшения приложений и избавления вас от зависимости от традиционной автоматизации.

Этот совет по миграции отправляет получателю приглашение на собрание. В нем показано, как отправить приглашение на собрание двумя способами:

- [Использование взаимодействия с Outlook](#sending-meeting-request-with-outlook-interop).
- [Использование Aspose.Email для Java](#advantages-of-using-asposeemail-for-java).

Мы также обсудим преимущества последнего подхода.

{{% /alert %}}
## **Отправка приглашения на собрание с помощью Outlook Interop**
Чтобы использовать классы Outlook, в вашем проекте.NET необходимо указать ссылку на Outlook.Interop. Ниже приведен фрагмент кода:

1. Создает приглашение на собрание.
1. Задает такие свойства, как объект, тело, местоположение и время.
1. Отправляет приглашение на собрание получателю.

Microsoft Outlook должен быть установлен в системе, где будет работать этот образец приложения.
### **Примеры программирования**
**C#**

~~~cs

// Create an instance of Outlook Application class

Outlook.Application outlookApp = new Outlook.Application ();

// Create an instance of AppointmentItem object and set the properties:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem) outlookApp.CreateItem (Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "subject of appointment";

oAppointment.Body = "body text of appointment";

oAppointment.Location = "Appointment location";

// Set the start date and end dates

oAppointment.Start = Convert.ToDateTime ("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Save the appointment

oAppointment.Save ();

// Send the appointment

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal ();

mailItem.To = "recipient@domain.com";

mailItem.Send();


~~~
## **Отправка приглашения на собрание с помощью Aspose.Email для Java**
Приведенный ниже код использует Aspose.Email для Java для отправки приглашения на собрание. Сначала создайте приглашение на собрание, используя [Встреча по электронной почте Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) класс. Затем отправьте электронное письмо, прикрепите приглашение на собрание и отправьте электронное письмо, используя [SMTP-клиент Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient) class.
### **Преимущества использования Aspose.Email для Java**
Outlook Interop требует установки Microsoft Outlook в системе, в которой он используется. Aspose.Email для Java не требует установки Microsoft Outlook и подходит для серверных приложений.
### **Примеры программирования**

~~~Java

// Create attendees of the meeting
MailAddressCollection attendees = new MailAddressCollection();
attendees.add("recipient1@domain.com");
attendees.add("recipient2@domain.com");

java.util.Calendar c = java.util.Calendar.getInstance();
Date startDate = c.getTime();
c.add(java.util.Calendar.HOUR_OF_DAY, 1);
Date endDate = c.getTime();

// Set up appointment
Appointment app = new Appointment(
    "Location", // location of meeting
    startDate, // start date
    endDate, // end date
    new MailAddress("organizer@domain.com"), // organizer
    attendees); // attendees

// Set up message that needs to be sent
MailMessage msg = new MailMessage();
msg.setFrom(new MailAddress("from@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setSubject("appointment request");
msg.setBody("you are invited");

// Add meeting request to the message
msg.addAlternateView(app.requestApointment());

// Set up the SMTP client to send email with meeting request
try (SmtpClient client = new SmtpClient("host", 25, "user", "password")) {
    client.send(msg);
}

~~~