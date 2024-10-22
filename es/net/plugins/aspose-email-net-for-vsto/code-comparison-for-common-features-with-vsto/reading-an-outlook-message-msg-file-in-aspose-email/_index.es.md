---
title: "Leer un archivo de mensaje de Outlook (MSG) en Aspose.Email"
url: /es/net/reading-an-outlook-message-msg-file-in-aspose-email/
weight: 190
type: docs
---


Para usar objetos de automatización de Office para Microsoft Outlook, necesita agregar referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook a su proyecto.
### **VSTO**
``` cs

 // Crear una nueva clase de aplicación

_Application outlook = new Outlook.Application();

// Crear un objeto MailItem

MailItem item = (MailItem)outlook.CreateItemFromTemplate("test.msg", Type.Missing);

// Acceder a diferentes campos del mensaje

System.Console.WriteLine(string.Format("Asunto:{0}", item.Subject));

System.Console.WriteLine(string.Format("Dirección de correo del remitente:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("Nombre del remitente:{0}", item.SenderName));

System.Console.WriteLine(string.Format("Para:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Cuerpo HTML:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Cuerpo de texto:{0}", item.Body));

```
### **Aspose.Email**
Para acceder a los objetos Aspose.Email.Outlook, necesita agregar una referencia a Aspose.Email a su proyecto.

``` cs

  // Crear asistentes de la reunión

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Configurar la cita

Appointment app = new Appointment(

    "Ubicación", // ubicación de la reunión

    DateTime.Now, // fecha de inicio

    DateTime.Now.AddHours(1), // fecha de fin

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
## **Descargar código de ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772943)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Reading.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](http://goo.gl/TpCQPp)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Reading%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)