---
title: "Envío de Solicitudes de Reunión Usando Outlook Interop y Aspose.Email para Java"
url: /es/java/sending-meeting-request-using-outlook-interop-and-aspose-email-for-java/
weight: 40
type: docs
---


{{% alert color="primary" %}} 

Nuestros consejos de migración muestran cómo los productos de Aspose pueden usarse para mejorar tus aplicaciones y liberarte de la dependencia de la automatización tradicional.

Este consejo de migración envía una solicitud de reunión a un destinatario. Demuestra cómo enviar solicitudes de reunión de dos maneras:

- [Usando Outlook Interop](#sending-meeting-request-with-outlook-interop).
- [Usando Aspose.Email para Java](#advantages-of-using-asposeemail-for-java).

También discutiremos las ventajas del segundo enfoque.

{{% /alert %}} 
## **Envío de Solicitudes de Reunión con Outlook Interop**
Para usar las clases de Outlook, Outlook.Interop debe ser referenciado en tu proyecto .NET. El fragmento de código a continuación:

1. Crea una solicitud de reunión.
1. Establece propiedades como asunto, cuerpo, ubicación y hora.
1. Envía la solicitud de reunión al destinatario.

Microsoft Outlook debe estar instalado en el sistema donde se ejecutará esta aplicación de ejemplo.
### **Ejemplos de Programación**
**C#**

~~~cs

// Crear una instancia de la clase Outlook Application

Outlook.Application outlookApp = new Outlook.Application ();

// Crear una instancia del objeto AppointmentItem y establecer las propiedades:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem) outlookApp.CreateItem (Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "asunto de la reunión";

oAppointment.Body = "texto del cuerpo de la reunión";

oAppointment.Location = "Ubicación de la reunión";

// Establecer la fecha y hora de inicio y fin

oAppointment.Start = Convert.ToDateTime ("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Guardar la reunión

oAppointment.Save ();

// Enviar la reunión

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal ();

mailItem.To = "recipient@domain.com";

mailItem.Send();


~~~
## **Envío de Solicitudes de Reunión Usando Aspose.Email para Java**
El código a continuación utiliza Aspose.Email para Java para enviar una solicitud de reunión. Primero, crea la solicitud de reunión utilizando la clase [Aspose.Email Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment). Luego envía el correo electrónico, adjunta la solicitud de reunión y envía el correo electrónico utilizando la clase [Aspose.Email SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient).
### **Ventajas de usar Aspose.Email para Java**
Outlook Interop requiere que Microsoft Outlook esté instalado en el sistema donde se utiliza. Aspose.Email para Java no requiere que Microsoft Outlook esté instalado y es adecuado para aplicaciones en servidor.
### **Ejemplos de Programación**

~~~Java

// Crear asistentes de la reunión
MailAddressCollection attendees = new MailAddressCollection();
attendees.add("recipient1@domain.com");
attendees.add("recipient2@domain.com");

java.util.Calendar c = java.util.Calendar.getInstance();
Date startDate = c.getTime();
c.add(java.util.Calendar.HOUR_OF_DAY, 1);
Date endDate = c.getTime();

// Configurar la cita
Appointment app = new Appointment(
    "Ubicación", // ubicación de la reunión
    startDate, // fecha de inicio
    endDate, // fecha de fin
    new MailAddress("organizer@domain.com"), // organizador
    attendees); // asistentes

// Configurar el mensaje que necesita ser enviado
MailMessage msg = new MailMessage();
msg.setFrom(new MailAddress("from@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setSubject("solicitud de reunión");
msg.setBody("estás invitado");

// Agregar la solicitud de reunión al mensaje
msg.addAlternateView(app.requestApointment());

// Configurar el cliente SMTP para enviar el correo electrónico con la solicitud de reunión
try (SmtpClient client = new SmtpClient("host", 25, "user", "password")) {
    client.send(msg);
}

~~~