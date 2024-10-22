---
title: "Recebendo Notificações para Mensagens Enviadas com Sucesso e Falhas"
url: /pt/java/receiving-notifications-for-successfully-sent-and-failed-messages/
weight: 90
type: docs
---


Quando você deseja receber a notificação de entrega tanto para mensagens enviadas com sucesso quanto para mensagens com falha, pode usar o operador pipe (|) para a propriedade [DeliveryNotificationOptions](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). O seguinte trecho de código mostra como receber notificações para mensagens enviadas com sucesso e mensagens falhas.



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