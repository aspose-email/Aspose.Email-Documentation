---
title: "Функции утилиты — SMTP-клиент"
url: /ru/net/utility-features-smtp-client/
weight: 30
type: docs
---

# Функции утилиты — SMTP-клиент

## **Список серверов расширений с использованием клиента Smtp**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) метод возвращает поддерживаемые типы расширений в виде строкового массива.

### **Получение серверных расширений**

В следующем фрагменте кода показано, как извлекать серверные расширения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}

## **Работа с подписанным сообщением**

Aspose.Email API предоставляет возможность создавать подписанные сообщения с использованием сертификатов. [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс можно использовать для подписи сообщения для сохранения или даже отправки его с помощью [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

### **Подпишите сообщение**

В следующем фрагменте кода показано, как подписать сообщение.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}

### **Использование опции «Отдельный сертификат»**

Веб-клиенты электронной почты могут не отображать основное содержимое подписанного сообщения. Эту проблему можно решить, отсоединив сертификат перед отправкой почтовым веб-клиентам. Отключенный флаг в перегруженном методе [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) могут быть использованы для достижения этой цели. Если установлено значение **true**, сертификат отделяется от электронного письма и наоборот. Чтобы увидеть текст подписанного сообщения в веб-клиентах, вам необходимо создать [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) с отдельной подписью. В следующем фрагменте кода показано, как использовать опцию отдельного сертификата.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}

## **Подтвердите учетные данные почтового сервера без отправки электронной почты**

Aspose.Email API предоставляет возможность проверки учетных данных почтового сервера без отправки электронного письма. Это может быть достигнуто с помощью [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentials/) метод, который отвечает за проверку подлинности и правильности предоставленных учетных данных электронной почты, которые обычно используются для аутентификации при подключении к серверу.

Он проверяет, действительны ли предоставленные учетные данные электронной почты, такие как имя пользователя и пароль, и что клиент может установить успешное соединение с сервером. Эта проверка учетных данных помогает обеспечить клиенту безопасный доступ к учетной записи электронной почты и выполнение различных операций, таких как отправка электронной почты.

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

Существует также версия метода [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentialsasync/)  для выполнения асинхронной операции. 