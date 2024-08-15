---
title: "Отправка сообщений электронной почты через MailGun и SendGrid"
url: /ru/net/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Отправка сообщений с помощью MailGun и SendGrid**

Aspose.Email предоставляет возможность отправлять сообщения электронной почты с помощью сервисов MailGun или SendGrid. Его унифицированный API позволяет инициализировать клиента, подготовить и отправить сообщение электронной почты.

Во-первых, важно настроить параметры в зависимости от того, какой сервис будет использоваться для отправки сообщений. [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) класс поможет вам в этом. В следующем примере кода показано, как настроить параметры сервисов.

*MailGun* варианты клиента:

```cs
string domain = "YOUR_MAILGUN_DOMEN";
string privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

*SendGrid* варианты клиента:

```cs
string privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
Чтобы подготовить и отправить сообщение, используйте следующий пример кода и шаги:

1. Создайте экземпляр [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/) interface.
2. Создайте новое eml-сообщение, используя [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Укажите его свойства.
3. Используйте [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) метод объекта клиента для отправки электронного письма. Результат операции отправки сохраняется в переменной resp.
4. Если операция отправки не была успешной (resp.successful имеет значение false), код переходит в цикл foreach для повторного просмотра коллекции ErrorMessages объекта resp. Каждое сообщение об ошибке выводится на консоль с помощью Console.WriteLine.

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
## **Асинхронная отправка сообщений**

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

