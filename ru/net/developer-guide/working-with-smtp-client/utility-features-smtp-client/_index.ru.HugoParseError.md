---
title: Утилитарные функции - SMTP Клиент
type: docs
weight: 30
url: /net/utility-features-smtp-client/
---

# Утилитарные функции - SMTP Клиент

## **Получение расширений сервера с помощью SMTP Клиента**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) позволяет получать расширения сервера, которые поддерживаются сервером, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для конкретной функциональности. Метод [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) возвращает поддерживаемые типы расширений в виде массива строк.

### **Получение расширений сервера**

Следующий код показывает, как получить расширения сервера.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}

## **Работа с подписанным сообщением**

API Aspose.Email предоставляет возможность создавать подписанные сообщения с использованием сертификатов. Метод [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) может быть использован для подписания сообщения с целью его сохранения или даже отправки с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

### **Подписать сообщение**

Следующий код показывает, как подписать сообщение.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}

### **Использование опции отсоединенного сертификата**

Веб-клиенты электронной почты могут не отображать содержимое тела подписанного сообщения. Это можно решить, отсоединив сертификат перед отправкой его веб-клиентам электронной почты. Флаг отсоединения в перегруженном методе [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) может быть использован для достижения этого. Если установить его в **true**, сертификат отсоединяется от электронной почты и наоборот. Чтобы увидеть тело подписанного сообщения в веб-клиентах, вам нужно создать [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) с отсоединенной подписью. Следующий код показывает, как использовать опцию отсоединенного сертификата.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}

## **Проверка учетных данных почтового сервера без отправки электронной почты**

API Aspose.Email предоставляет возможность проверить учетные данные почтового сервера без отправки электронной почты. Это можно сделать с помощью метода [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentials/), который отвечает за проверку подлинности и правильности предоставленных учетных данных электронной почты, которые обычно используются для аутентификации при подключении к серверу.

Он проверяет, что предоставленные учетные данные электронной почты, такие как имя пользователя и пароль, являются действительными, и что клиент может установить успешное соединение с сервером. Эта проверка учетных данных помогает гарантировать, что клиент может безопасно получить доступ к учетной записи электронной почты и выполнять различные операции, такие как отправка электронной почты.

```cs
using (SmtpClient client = new SmtpClient(server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Также существует версия метода [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentialsasync/) для выполнения асинхронной операции.