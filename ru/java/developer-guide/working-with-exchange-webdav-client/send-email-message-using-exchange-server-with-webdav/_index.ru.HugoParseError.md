---
title: Отправка электронного сообщения с использованием Exchange Server через WebDav
type: docs
weight: 100
url: /java/send-email-message-using-exchange-server-with-webdav/
---

Вы можете отправлять электронные сообщения, используя Exchange Server, с помощью инструментов в com.aspose.email. Метод [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) принимает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять электронные сообщения, используя клиент Exchange API.
## **Отправка электронных сообщений с использованием Exchange WebDav**
Чтобы отправить электронные письма с использованием Exchange Server:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Создайте экземпляр класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Укажите свойства from, to, subject и другие свойства [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Вызовите метод [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) для отправки электронной почты.

Пример кода ниже отправляет электронные сообщения с использованием Exchange Server.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}