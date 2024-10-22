---
title: "Enviar mensajes de correo electrónico a través de MailGun y SendGrid"
url: /es/net/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Envío de mensajes utilizando MailGun y SendGrid**

Aspose.Email proporciona la capacidad de enviar mensajes de correo electrónico utilizando los servicios de MailGun o SendGrid. Su API unificada te permite inicializar un cliente, preparar y enviar el mensaje de correo electrónico.

Primero, es importante configurar las opciones dependiendo de qué servicio se va a utilizar para enviar los mensajes. La clase [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) te ayudará con eso. El siguiente ejemplo de código muestra cómo configurar opciones para los servicios.

Opciones del cliente *MailGun*:

```cs
string domain = "YOUR_MAILGUN_DOMEN";
string privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

Opciones del cliente *SendGrid*:

```cs
string privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
Para preparar y enviar un mensaje, utiliza el siguiente ejemplo de código y pasos:

1. Crea una instancia de la interfaz [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/).
2. Crea un nuevo mensaje eml usando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Especifica sus propiedades.
3. Utiliza el método [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) del objeto cliente para enviar el correo electrónico. El resultado de la operación de envío se almacena en la variable resp.
4. Si la operación de envío no fue exitosa (resp.Successful es false), el código entra en un bucle foreach para iterar sobre la colección ErrorMessages del objeto resp. Cada mensaje de error se imprime en la consola utilizando Console.WriteLine.

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
## **Envío de mensajes de forma asíncrona**

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