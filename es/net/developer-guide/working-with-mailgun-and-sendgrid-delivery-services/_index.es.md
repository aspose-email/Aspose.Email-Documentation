---
title: "Enviar mensajes de correo electrónico a través de MailGun y SendGrid"
url: /es/net/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Envío de mensajes con MailGun y SendGrid**

Aspose.Email ofrece la posibilidad de enviar mensajes de correo electrónico mediante los servicios MailGun o SendGrid. Su API unificada le permite inicializar un cliente, preparar y enviar el mensaje de correo electrónico.

En primer lugar, es importante configurar las opciones según el servicio que se vaya a utilizar para enviar mensajes. [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) la clase te ayudará con eso. El siguiente ejemplo de código muestra cómo configurar las opciones de los servicios.

*MailGun* opciones de cliente:

```cs
string domain = "YOUR_MAILGUN_DOMEN";
string privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

*SendGrid* opciones de cliente:

```cs
string privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
Para preparar y enviar un mensaje, sigue los pasos y ejemplos de código siguientes:

1. Crea una instancia del [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/) interface.
2. Crea un nuevo mensaje de eml usando el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Especifique sus propiedades.
3. Usa el [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) método del objeto cliente para enviar el correo electrónico. El resultado de la operación de envío se almacena en la variable resp.
4. Si la operación de envío no se realizó correctamente (resp.Successful es falso), el código introduce un bucle foreach para iterar sobre la colección ErrorMessages del objeto resp. Cada mensaje de error se imprime en la consola mediante Console.WriteLine.

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
## **Envío de mensajes de forma asincrónica**

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

