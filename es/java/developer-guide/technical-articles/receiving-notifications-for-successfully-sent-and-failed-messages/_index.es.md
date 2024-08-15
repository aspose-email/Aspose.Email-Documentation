---
title: "Recepción de notificaciones de mensajes enviados correctamente y con errores"
url: /es/java/receiving-notifications-for-successfully-sent-and-failed-messages/
weight: 90
type: docs
---


Si desea recibir la notificación de entrega de los mensajes enviados correctamente y de los mensajes fallidos, puede utilizar el operador pipe (|) para [DeliveryNotificationOptions](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) propiedad del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. En el siguiente fragmento de código, se muestra cómo recibir notificaciones de mensajes enviados correctamente y mensajes fallidos.



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