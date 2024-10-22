---
title: "Enviar Mensagens de Email via MailGun e SendGrid"
url: /pt/net/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Enviando Mensagens usando MailGun e SendGrid**

Aspose.Email fornece a capacidade de enviar mensagens de email usando os serviços MailGun ou SendGrid. Sua API unificada permite que você inicialize um cliente, prepare e envie a mensagem de email.

Primeiro, é importante configurar opções dependendo de qual serviço será usado para enviar mensagens. A classe [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) ajudará você com isso. O seguinte exemplo de código mostra como configurar opções para os serviços.

Opções do cliente *MailGun*:

```cs
string domain = "SEU_DOMÍNIO_MAILGUN";
string privApiKey = "SUA_CHAVE_API_PRIVADA_MAILGUN";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

Opções do cliente *SendGrid*:

```cs
string privApiKey = "SUA_CHAVE_API_PRIVADA_SENDGRID";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
Para preparar e enviar uma mensagem, use o seguinte exemplo de código e etapas:

1. Crie uma instância da interface [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/).
2. Crie uma nova mensagem em formato eml usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Especifique suas propriedades.
3. Use o método [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) do objeto cliente para enviar o email. O resultado da operação de envio é armazenado na variável resp.
4. Se a operação de envio não foi bem-sucedida (resp.Successful é falso), o código entra em um loop foreach para iterar sobre a coleção ErrorMessages do objeto resp. Cada mensagem de erro é impressa no console usando Console.WriteLine.

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
## **Enviando Mensagens de forma Assíncrona**

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