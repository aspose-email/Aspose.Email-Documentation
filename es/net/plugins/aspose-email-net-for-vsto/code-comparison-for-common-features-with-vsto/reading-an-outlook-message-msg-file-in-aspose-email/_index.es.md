---
title: "Lectura de un archivo de mensajes de Outlook (MSG) en Aspose.Email"
url: /es/net/reading-an-outlook-message-msg-file-in-aspose-email/
weight: 190
type: docs
---


Para usar objetos de automatización de oficina para Microsoft Outlook, debe agregar referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook a su proyecto.
### **VSTO**
``` cs

 // Create a new Application Class

_Application outlook = new Outlook.Application();

// Create a MailItem object

MailItem item = (MailItem)outlook.CreateItemFromTemplate("test.msg", Type.Missing);

// Access different fields of the message

System.Console.WriteLine(string.Format("Subject:{0}", item.Subject));

System.Console.WriteLine(string.Format("Sender Email Address:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("SenderName:{0}", item.SenderName));

System.Console.WriteLine(string.Format("TO:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Html Body:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Text Body:{0}", item.Body));

```
### **Aspose.Email**
Para acceder a los objetos Aspose.Email.Outlook, debe agregar una referencia a Aspose.Email a su proyecto.

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
## **Descargar código de muestra**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772943)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Reading.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](http://goo.gl/TpCQPp)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Reading%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)
