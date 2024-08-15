---
title: "Envío de la solicitud de reunión"
url: /es/net/sending-meeting-request/
weight: 200
type: docs
---


## **VSTO**
Para usar las clases de Outlook, se debe hacer referencia a Outlook.Interop en su proyecto de.NET. El siguiente fragmento de código:

1. Crea una convocatoria de reunión.
1. Establece propiedades como el tema, el cuerpo, la ubicación y la hora.
1. Envía la convocatoria de reunión al destinatario.
1. Microsoft Outlook debe estar instalado en el sistema en el que se ejecutará esta aplicación de ejemplo.

``` cs

 // Create an instance of Outlook Application class

Outlook.Application outlookApp = new Outlook.Application();

// Create an instance of AppointmentItem object and set the properties:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem)outlookApp.CreateItem(Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "subject of appointment";

oAppointment.Body = "body text of appointment";

oAppointment.Location = "Appointment location";

// Set the start date and end dates

oAppointment.Start = Convert.ToDateTime("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Save the appointment

oAppointment.Save();

// Send the appointment

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal();

mailItem.To = "recipient@domain.com";

mailItem.Send();

```
## **Aspose.Email**
El siguiente código usa Aspose.Email para.NET para enviar una convocatoria de reunión. En primer lugar, cree la convocatoria de reunión con la clase Aspose.Email.Appointment. A continuación, envíe el correo electrónico, adjunte la convocatoria de reunión y envíe el correo electrónico con la clase Aspose.Email.Mail.SmtpClient.

Ventajas de usar Aspose.Email para.NET

Outlook Interop requiere que Microsoft Outlook esté instalado en el sistema en el que se usa. Aspose.Email para.NET no requiere la instalación de Microsoft Outlook y es adecuado para aplicaciones de servidor.

``` cs

  // Create attendees of the meeting

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Set up appointment

Appointment app = new Appointment(

    "Location", // location of meeting

    DateTime.Now, // start date

    DateTime.Now.AddHours(1), // end date

    new MailAddress("organizer@domain.com"), // organizer

    attendees); // attendees

// Set up message that needs to be sent

MailMessage msg = new MailMessage();

msg.From = "from@domain.com";

msg.To = "to@domain.com";

msg.Subject = "appointment request";

msg.Body = "you are invited";

// Add meeting request to the message

msg.AddAlternateView(app.RequestApointment());

// Set up the SMTP client to send email with meeting request

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");

client.Send(msg);

```
##**Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772944)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Sending.Meeting.Request.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Sending%20Meeting%20Request%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Sending%20Meeting%20Request%20\(Aspose.Email\).zip)
