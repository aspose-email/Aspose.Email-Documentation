---
title: "Функции утилиты — клиент IMAP"
url: /ru/net/utility-features-imap-client/
weight: 100
type: docs
---

## **Подтвердить учетные данные почтового сервера**

Aspose.Email API позволяет проверять учетные данные почтового сервера без отправки электронного письма. [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentials) метод отвечает за проверку подлинности и действительности предоставленных учетных данных электронной почты, которые обычно используются для аутентификации при подключении к серверу.

Он проверяет, что предоставленные учетные данные электронной почты, такие как имя пользователя и пароль, действительны и что клиент может установить успешное соединение с сервером. Эта проверка учетных данных помогает обеспечить клиенту безопасный доступ к учетной записи электронной почты и выполнение различных операций, таких как получение электронной почты.

```cs
using (ImapClient client = new ImapClient(server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
  
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Для асинхронной операции также существует версия метода [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentialsasync).
