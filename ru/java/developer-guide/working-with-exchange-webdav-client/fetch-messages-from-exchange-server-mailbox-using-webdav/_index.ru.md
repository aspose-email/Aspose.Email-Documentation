---
title: "Извлечение сообщений из почтового ящика Exchange Server с использованием WebDav"
url: /ru/java/fetch-messages-from-exchange-server-mailbox-using-webdav/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Для получения списка сообщений в почтовом ящике Exchange Server использовался метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)). Метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) получает основную информацию о сообщениях, например, тему, идентификатор сообщения, отправителя и получателя.

Чтобы получить полные сведения о сообщении, Aspose.Email.Exchange предоставляет метод [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage). Класс [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) предоставляет подробности сообщения, такие как тело, заголовки и вложения.

{{% /alert %}} 
## **Извлечение сообщений из почтового ящика Exchange Server**
Чтобы извлечь сообщения из почтового ящика Exchange Server:

1. Создайте экземпляр типа [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Вызовите метод [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) для получения [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Переберите коллекцию [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) для получения значений [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)).
1. Вызовите [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) и передайте [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) в качестве параметра.

Следующий фрагмент кода подключается к почтовому ящику Exchange Server и извлекает все сообщения.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}