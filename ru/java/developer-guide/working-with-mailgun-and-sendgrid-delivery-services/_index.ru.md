---
title: "Отправка электронной почты через MailGun и SendGrid на Java"
url: /ru/java/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Отправка сообщений с помощью MailGun и SendGrid**

Aspose.Email предоставляет унифицированный API для отправки сообщений электронной почты с помощью сервисов MailGun или SendGrid. API позволяет инициализировать клиента, подготовить и отправить сообщение электронной почты.

Во-первых, важно настроить параметры в зависимости от того, какой сервис будет использоваться для отправки сообщений. С помощью [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/) класс, задайте параметры DeliveryServiceClient. В следующем примере кода показано, как настроить параметры сервисов.

**Клиент MailGun** options:

```java
String domain = "YOUR_MAILGUN_DOMEN";
String privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**Клиент SendGrid** options:

```java
String privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
Затем вызовите требуемый экземпляр клиента с помощью конструктора.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Наконец, подготовьте и отправьте сообщение по электронной почте.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```


