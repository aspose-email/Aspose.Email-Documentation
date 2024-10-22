---
title: "Recibir Notificaciones de Mensajes Enviados con Éxito y Fallidos"
url: /es/java/recibiendo-notificaciones-para-mensajes-enviados-con-exito-y-fallidos/
weight: 90
type: docs
---


Cuando deseas recibir la notificación de entrega tanto para mensajes enviados con éxito como para los fallidos, puedes usar el operador de pipe (|) para la propiedad [DeliveryNotificationOptions](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). El siguiente fragmento de código te muestra cómo recibir notificaciones para mensajes enviados con éxito y fallidos.



~~~Java
// Create the message
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@receiver.com"));
msg.setSubject("the subject of the message");

// Set delivery notifications for success and failed messages and Add the MIME headers
msg.setDeliveryNotificationOptions(DeliveryNotificationOptions.OnSuccess | DeliveryNotificationOptions.OnFailure);
msg.getHeaders().add("Read-Receipt-To", "sender@sender.com");
msg.getHeaders().add("Disposition-Notification-To", "sender@sender.com");

// Send the message
SmtpClient client = new SmtpClient("host", "username", "password");
client.send(msg);
~~~