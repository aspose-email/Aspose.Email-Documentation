---
title: "Получение уведомлений об успешно отправленных и неудачных сообщениях"
url: /ru/java/receiving-notifications-for-successfully-sent-and-failed-messages/
weight: 90
type: docs
---


Если вы хотите получить уведомление о доставке как успешно отправленных, так и ошибочных сообщений, вы можете использовать оператор pipe (|) для [DeliveryNotificationOptions](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) собственность [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. В следующем фрагменте кода показано, как получать уведомления об успешно отправленных и неудачных сообщениях.



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