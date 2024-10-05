---
title: "Отправка электронной почты через MailGun и SendGrid на Java"
url: /ru/java/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Отправка сообщений с использованием MailGun и SendGrid**

Aspose.Email предоставляет унифицированный API для отправки электронных писем с использованием услуг MailGun или SendGrid. API позволяет инициализировать клиента, подготовить и отправить электронное сообщение.

Сначала важно настроить параметры в зависимости от того, какая служба будет использоваться для отправки сообщений. С помощью класса [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/) установите параметры DeliveryServiceClient. Следующий образец кода покажет, как настроить параметры для служб.

**Параметры клиента MailGun**:

```java
String domain = "YOUR_MAILGUN_DOMEN";
String privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**Параметры клиента SendGrid**:

```java
String privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
Затем вызовите необходимый экземпляр клиента, используя строитель.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Наконец, подготовьте и отправьте электронное сообщение.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```