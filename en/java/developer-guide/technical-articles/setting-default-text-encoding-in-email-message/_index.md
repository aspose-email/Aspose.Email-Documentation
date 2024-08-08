---
title: Setting Default Text Encoding in Email Message
type: docs
weight: 120
url: /java/setting-default-text-encoding-in-email-message/
---


This article introduces the [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) property and explains how it is used. Using this property, you can set the default text encoding for the following properties:

- From: Display name
- To: Display name
- Subject
- Body
## **Setting Default Text Encoding**
In previous versions of Aspose.Email, text encoding for the from, to, subject and body properties were set separately. To improve usability, we added the [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) property which sets all at once. It's now easier to ensure that all the text in the above properties is encoded properly in the email message. The following code snippet shows you how to use a French word as the display name for email addresses, subject and body.



~~~Java
// Create an instance of MailMessage
String fileName = "data/";
MailMessage msg = new MailMessage();

// Set the default or preferred encoding. This encoding will be used as the default for the from/to email addresses, subject and body of message.
msg.setPreferredTextEncoding(Charset.forName("cp1252"));

// Set email addresses, subject and body
msg.setFrom(new MailAddress("dmo@domain.com", "démo"));
msg.getTo().addItem(new MailAddress("dmo@domain.com", "démo"));
msg.setSubject("démo");
msg.setHtmlBody("démo");
msg.save(fileName + "SetDefaultTextEncoding_out.msg", SaveOptions.getDefaultMsg());
~~~