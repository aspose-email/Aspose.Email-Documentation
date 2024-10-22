---
title: "Enviando Solicitud de Reunión"
url: /es/net/sending-meeting-request/
weight: 200
type: docs
---


## **VSTO**
Para usar las clases de Outlook, Outlook.Interop debe ser referenciado en su proyecto .NET. El fragmento de código a continuación:

1. Crea una solicitud de reunión.
1. Establece propiedades como asunto, cuerpo, ubicación y hora.
1. Envía la solicitud de reunión al destinatario.
1. Microsoft Outlook debe estar instalado en el sistema donde se ejecutará esta aplicación de muestra.

``` cs

 // Crear una instancia de la clase Outlook Application

Outlook.Application outlookApp = new Outlook.Application();

// Crear una instancia del objeto AppointmentItem y establecer las propiedades:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem)outlookApp.CreateItem(Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "asunto de la reunión";

oAppointment.Body = "texto del cuerpo de la reunión";

oAppointment.Location = "Ubicación de la reunión";

// Establecer la fecha de inicio y las fechas de finalización

oAppointment.Start = Convert.ToDateTime("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Guardar la cita

oAppointment.Save();

// Enviar la cita

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal();

mailItem.To = "recipient@domain.com";

mailItem.Send();

```
## **Aspose.Email**
El código a continuación utiliza Aspose.Email para .NET para enviar una solicitud de reunión. Primero, crea la solicitud de reunión utilizando la clase Aspose.Email.Appointment. Luego, envía el correo electrónico, adjunta la solicitud de reunión y envía el correo electrónico utilizando la clase Aspose.Email.Mail.SmtpClient.

Ventajas de usar Aspose.Email para .NET

Outlook Interop requiere que Microsoft Outlook esté instalado en el sistema donde se usa. Aspose.Email para .NET no requiere que Microsoft Outlook esté instalado y es adecuado en aplicaciones de servidor.

``` cs

  // Crear asistentes a la reunión

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Configurar la cita

Appointment app = new Appointment(

    "Ubicación", // ubicación de la reunión

    DateTime.Now, // fecha de inicio

    DateTime.Now.AddHours(1), // fecha de finalización

    new MailAddress("organizer@domain.com"), // organizador

    attendees); // asistentes

// Configurar el mensaje que necesita ser enviado

MailMessage msg = new MailMessage();

msg.From = "from@domain.com";

msg.To = "to@domain.com";

msg.Subject = "solicitud de cita";

msg.Body = "estás invitado";

// Agregar solicitud de reunión al mensaje

msg.AddAlternateView(app.RequestApointment());

// Configurar el cliente SMTP para enviar el correo electrónico con la solicitud de reunión

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");

client.Send(msg);

```
##**Descargar Código de Muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772944)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Sending.Meeting.Request.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Sending%20Meeting%20Request%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Sending%20Meeting%20Request%20\(Aspose.Email\).zip)