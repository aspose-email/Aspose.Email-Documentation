---
title: "Envío de una convocatoria de reunión mediante Outlook Interop y Aspose.Email para Java"
url: /es/java/sending-meeting-request-using-outlook-interop-and-aspose-email-for-java/
weight: 40
type: docs
---


{{% alert color="primary" %}}

Nuestros consejos de migración muestran cómo se pueden usar los productos de Aspose para mejorar sus aplicaciones y liberarlo de la dependencia de la automatización tradicional.

Este consejo de migración envía una convocatoria de reunión a un destinatario. Muestra cómo enviar una convocatoria de reunión de dos maneras:

- [Uso de Outlook Interop](#sending-meeting-request-with-outlook-interop).
- [Uso de Aspose.Email para Java](#advantages-of-using-asposeemail-for-java).

También analizaremos las ventajas de este último enfoque.

{{% /alert %}}
## **Envío de una convocatoria de reunión con Outlook Interop**
Para usar las clases de Outlook, se debe hacer referencia a Outlook.Interop en su proyecto de.NET. El siguiente fragmento de código:

1. Crea una convocatoria de reunión.
1. Establece propiedades como el tema, el cuerpo, la ubicación y la hora.
1. Envía la convocatoria de reunión al destinatario.

Microsoft Outlook debe estar instalado en el sistema en el que se ejecutará esta aplicación de ejemplo.
### **Ejemplos de programación**
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
## **Envío de una convocatoria de reunión mediante Aspose.Email para Java**
El siguiente código usa Aspose.Email para Java para enviar una convocatoria de reunión. En primer lugar, cree la convocatoria de reunión mediante el [Aspose.Cita por correo electrónico](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) clase. A continuación, envíe el correo electrónico, adjunte la convocatoria de reunión y envíe el correo electrónico mediante [Cliente SMTP Aspose.Email](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient) class.
### **Ventajas de usar Aspose.Email para Java**
Outlook Interop requiere que Microsoft Outlook esté instalado en el sistema en el que se usa. Aspose.Email para Java no requiere la instalación de Microsoft Outlook y es adecuado para aplicaciones de servidor.
### **Ejemplos de programación**

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