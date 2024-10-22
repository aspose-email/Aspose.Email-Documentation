---
title: "Enviar correo electrónico a través de MailGun y SendGrid en Java"
url: /es/java/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Enviando mensajes usando MailGun y SendGrid**

Aspose.Email proporciona una API unificada para enviar mensajes de correo electrónico utilizando los servicios de MailGun o SendGrid. La API te permite inicializar un cliente, preparar y enviar el mensaje de correo electrónico.

Primero, es importante configurar las opciones dependiendo de qué servicio se va a utilizar para enviar mensajes. Con la clase [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/), establece los parámetros del DeliveryServiceClient. El siguiente ejemplo de código te mostrará cómo configurar las opciones para los servicios.

**Opciones del cliente de MailGun**:

```java
String domain = "YOUR_MAILGUN_DOMEN";
String privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**Opciones del cliente de SendGrid**:

```java
String privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
Luego, llama a la instancia del cliente requerida utilizando el constructor.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Finalmente, prepara y envía un mensaje de correo electrónico.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```