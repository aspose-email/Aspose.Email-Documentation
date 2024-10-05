---
title: "Отправка электронных сообщений через MailGun и SendGrid"
url: /ru/net/send-email-messages-via-mailgun-and-sendgrid/
weight: 10
type: docs
---

## **Отправка сообщений с использованием MailGun и SendGrid**

Aspose.Email предоставляет возможность отправки электронных сообщений с использованием сервисов MailGun или SendGrid. Его унифицированный API позволяет инициализировать клиент, подготавливать и отправлять электронное сообщение.

Сначала важно настроить параметры в зависимости от сервиса, который будет использоваться для отправки сообщений. Класс [DeliveryServiceOptions](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/deliveryserviceoptions/) поможет вам с этим. Следующий пример кода показывает, как настроить параметры для сервисов.

*Опции клиента MailGun*:

```cs
string domain = "YOUR_MAILGUN_DOMEN";
string privApiKey = "YOUR_MAILGUN_PRIVATE_API_KEY";
var opt = new MailgunClientOptions { Domain = domain, ApiKey = privApiKey };
```

*Опции клиента SendGrid*:

```cs
string privApiKey = "YOUR_SENDGRID_PRIVATE_API_KEY";
var opt = new SendGridClientOptions { ApiKey = privApiKey };
```
Чтобы подготовить и отправить сообщение, используйте следующий пример кода и шаги:

1. Создайте экземпляр интерфейса [IDeliveryServiceClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/).
2. Создайте новое сообщение eml, используя класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Укажите его свойства.
3. Используйте метод [Send](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice/ideliveryserviceclient/send/#ideliveryserviceclientsend-method) объекта клиента для отправки электронной почты. Результат операции отправки сохраняется в переменной resp.
4. Если операция отправки не была успешной (resp.Successful равно false), код enters enters цикл foreach для перебора коллекции ErrorMessages объекта resp. Каждое сообщение об ошибке выводится на консоль с помощью Console.WriteLine.

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