---
title: "Получение сведений о почтовом ящике с помощью клиента WebDAV"
url: /ru/java/getting-mailbox-information-using-webdav-client/
weight: 50
type: docs
---

{{% alert color="primary" %}}

The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) класс содержит элементы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange путем вызова [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) метод. Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Получайте информацию о почтовом ящике из таких объектов, как [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) , и [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).

В этой статье показано, как получить доступ к данным почтового ящика непосредственно с сервера Exchange.

{{% /alert %}}
## **Получение сведений о почтовом ящике с сервера Exchange**
Чтобы получить информацию о почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Укажите сервер Exchange, имя пользователя, пароль и домен в конструкторе ExchangeClient.
1. Позвоните [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) метод получения размера почтового ящика.
1. Позвоните [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) метод получения экземпляра [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class.
1. Получите информацию о почтовом ящике с помощью [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) различные свойства класса.

Приведенные ниже примеры кодов содержат информацию о почтовом ящике Exchange.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}
