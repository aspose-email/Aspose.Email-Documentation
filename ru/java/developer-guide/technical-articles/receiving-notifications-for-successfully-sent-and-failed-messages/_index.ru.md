---
title: "Получение уведомлений о успешно отправленных и неудачных сообщениях"
url: /ru/java/receiving-notifications-for-successfully-sent-and-failed-messages/
weight: 90
type: docs
---


Когда вы хотите получать уведомления о доставке как для успешно отправленных, так и для неудачных сообщений, вы можете использовать оператор pipe (|) для свойства [DeliveryNotificationOptions](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Следующий фрагмент кода показывает, как получать уведомления о successfully sent и failed сообщения.


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