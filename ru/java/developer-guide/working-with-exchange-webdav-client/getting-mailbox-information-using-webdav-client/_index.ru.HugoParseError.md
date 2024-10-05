---
title: Получение информации о почтовом ящике с помощью WebDav клиента
type: docs
weight: 50
url: /java/getting-mailbox-information-using-webdav-client/
---

{{% alert color="primary" %}} 

Класс [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) имеет члены, которые можно использовать для получения информации о почтовом ящике с сервера Exchange, вызывая метод [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)). Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Получите информацию о почтовом ящике из свойств, таких как [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) и [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).

В этой статье показано, как получить информацию о почтовом ящике напрямую с сервера Exchange.

{{% /alert %}} 
## **Получение информации о почтовом ящике с сервера Exchange**
Чтобы получить информацию о почтовом ящике Exchange:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Укажите сервер Exchange, имя пользователя, пароль и домен в конструкторе ExchangeClient.
1. Вызовите метод [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) для получения размера почтового ящика.
1. Вызовите метод [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) для получения экземпляра класса [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo).
1. Получите информацию о почтовом ящике, используя различные свойства класса [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo).

Примеры кода ниже получают информацию о почтовом ящике Exchange.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}