---
title: Send Email via MailGun and SendGrid in Java
type: docs
weight: 10
url: /java/send-email-messages-via-mailgun-and-sendgrid/
---

## **Sending Messages using MailGun and SendGrid**

Aspose.Email provides a unified API to send email messages using MailGun or SendGrid services. The API allows you to initialize a client, prepare and send the email message. 

First, it's important to set up options depending on which service is going to be used for sending messages. With the [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/) class, set the DeliveryServiceClient parameters. The following code sample will show you how to set up options for the services.

**MailGun client** options:

```java
String domain = "YOUR_MAILGUN_DOMEN";
String privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**SendGrid client** options:

```java
String privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
Then, call the required client instance using the builder.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Finally, prepare and send an email message.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```


