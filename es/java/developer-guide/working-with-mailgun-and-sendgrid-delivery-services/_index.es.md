---
title: "Enviar correo electrónico a través de MailGun y SendGrid en Java"
url: /es/java/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Envío de mensajes con MailGun y SendGrid**

Aspose.Email proporciona una API unificada para enviar mensajes de correo electrónico mediante los servicios MailGun o SendGrid. La API le permite inicializar un cliente, preparar y enviar el mensaje de correo electrónico.

En primer lugar, es importante configurar las opciones según el servicio que se vaya a utilizar para enviar mensajes. Con el [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/) clase, establezca los parámetros de DeliveryServiceClient. El siguiente ejemplo de código le mostrará cómo configurar las opciones de los servicios.

**Cliente MailGun** options:

```java
String domain = "YOUR_MAILGUN_DOMEN";
String privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**Cliente SendGrid** options:

```java
String privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
A continuación, llame a la instancia de cliente requerida mediante el generador.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Por último, prepare y envíe un mensaje de correo electrónico.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```


