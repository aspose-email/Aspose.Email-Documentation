---
title: "Enviar E-mail via MailGun e SendGrid em Java"
url: /pt/java/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Enviando Mensagens Usando MailGun e SendGrid**

Aspose.Email fornece uma API unificada para enviar mensagens de e-mail usando os serviços MailGun ou SendGrid. A API permite que você inicialize um cliente, prepare e envie a mensagem de e-mail. 

Primeiro, é importante configurar as opções dependendo de qual serviço será usado para enviar mensagens. Com a classe [DeliveryServiceOptions](https://reference.aspose.com/email/java/com.aspose.email/deliveryserviceoptions/), defina os parâmetros do DeliveryServiceClient. O seguinte exemplo de código mostrará como configurar opções para os serviços.

**Opções do cliente MailGun:**

```java
String domain = "SEU_DOMÍNIO_MAILGUN";
String privApiKey = "SUA_CHAVE_API_PRIVADA_MAILGUN";
MailgunClientOptions opt = new MailgunClientOptions();
opt.setDomain(domain);
opt.setApiKey(privApiKey);
```

**Opções do cliente SendGrid:**

```java
String privApiKey = "SUA_CHAVE_API_PRIVADA_SENDGRID";
SendGridClientOptions opt = new SendGridClientOptions();
opt.setApiKey(privApiKey);
```
Em seguida, chame a instância do cliente necessária usando o construtor.

```java
IDeliveryServiceClient client = DeliveryServiceClientFactory.get(opt);
```
Por fim, prepare e envie uma mensagem de e-mail.

```java
MailMessage eml = new MailMessage("fromAddress", "toAddress", "subject", "body");

DeliveryServiceResponse resp = client.send(eml);

if (!resp.isSuccessful()) {
    for (String error : resp.getErrorMessages()) {
        System.out.println(error);
    }
}
```