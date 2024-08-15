---
title: Send Email Messages via MailGun and SendGrid
type: docs
weight: 10
url: /net/send-email-messages-via-mailgun-and-sendgrid/
---

## **Sending Messages using MailGun and SendGrid**

Aspose.Email provides the ability to send email messages using MailGun or SendGrid services. Its unified API allows you to initialize a client, prepare and send the email message. 

First, it's important to set up options depending on which service is going to be used for sending messages. [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) class will help you with that. The following code sample shows how to set up options for the services.

*MailGun* client options:

```cs
string domain = "YOUR_MAILGUN_DOMEN";
string privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

*SendGrid* client options:

```cs
string privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
To prepare and send a message, use the following code sample and steps:

1. Create an instance of the [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/) interface. 
2. Create a new eml message using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. Specify its properties.
3. Use the [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) method of the client object to send the email. The result of the send operation is stored in the resp variable.
4. If the sending operation was not successful (resp.Successful is false), the code enters a foreach loop to iterate over the ErrorMessages collection of the resp object. Each error message is printed to the console using Console.WriteLine.

```cs
IDeliveryServiceClient client = DeliveryServiceClientFactory.Get(opt);

MailMessage eml = new MailMessage(fromAddress, toAddress, subject, body);

var resp = client.Send(eml);

if (!resp.Successful)
{
    foreach (var error in resp.ErrorMessages)
    {
        Console.WriteLine(error);
    }
}
```
## **Sending Messages Asynchronously**

```cs
MailMessage eml = new MailMessage(fromAddress, toAddress, subject, body);

var sendTask = client.SendAsync(eml);
sendTask.Wait();

if (!sendTask.Result.Successful)
{
    foreach (var error in sendTask.Result.ErrorMessages)
    {
        Console.WriteLine(error);
    }
}
```

