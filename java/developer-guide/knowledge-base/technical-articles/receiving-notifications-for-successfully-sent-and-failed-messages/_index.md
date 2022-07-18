---
title: Receiving Notifications for Successfully Sent and Failed Messages
type: docs
weight: 90
url: /java/receiving-notifications-for-successfully-sent-and-failed-messages/
---


When you want to get the delivery notification for both successfully sent and failed messages, you can use the pipe (|) operator for the [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDeliveryNotificationOptions\(\)) property of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage) class. The following code snippet shows you how to receive notifications for successfully sent and failed messages.



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