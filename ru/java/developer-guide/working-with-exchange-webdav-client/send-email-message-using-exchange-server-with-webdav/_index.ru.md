---
title: "Отправка сообщения электронной почты с помощью сервера Exchange с WebDAV"
url: /ru/java/send-email-message-using-exchange-server-with-webdav/
weight: 100
type: docs
---

Вы можете отправлять сообщения электронной почты с помощью сервера Exchange с помощью инструментов com.aspose.email. [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) метод принимает [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) экземпляр в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять сообщения электронной почты с помощью клиента Exchange или API.
## **Отправка сообщений электронной почты с помощью Exchange WebDAV**
Чтобы отправить электронные письма с помощью сервера Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Создайте экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.
1. Укажите откуда, куда, тему и прочее [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) properties.
1. Позвоните [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) способ отправки электронного письма.

Приведенный ниже пример кода отправляет сообщения электронной почты с помощью Exchange Server.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}
