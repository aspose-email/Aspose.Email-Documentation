---
title: "Утилитарные функции - POP3 клиент"
url: /ru/net/utility-features-pop3-client/
weight: 10
type: docs
---

## **Подтвердить учетные данные почтового сервера**

Метод [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentials) API Aspose.Email позволяет проверить учетные данные почтового сервера без отправки электронного письма. Этот метод отвечает за проверку подлинности и действительности предоставленных учетных данных электронной почты, используемых для аутентификации при подключении к серверу.

Он проверяет, что учетные данные электронной почты, такие как имя пользователя и пароль, действительны и что клиент может установить успешное соединение с сервером. Эта проверка учетных данных помогает обеспечить безопасный доступ клиента к учетной записи электронной почты и выполнять различные операции, такие как получение электронной почты.

```cs
using (Pop3Client client = new Pop3Client(server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Для выполнения асинхронной операции также существует версия метода [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentialsasync/).