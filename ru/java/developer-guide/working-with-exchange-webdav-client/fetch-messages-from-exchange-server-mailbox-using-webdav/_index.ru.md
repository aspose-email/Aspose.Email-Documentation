---
title: "Получение сообщений из почтового ящика сервера Exchange с помощью WebDAV"
url: /ru/java/fetch-messages-from-exchange-server-mailbox-using-webdav/
weight: 30
type: docs
---

{{% alert color="primary" %}}

При перечислении сообщений на сервере Exchange использовалось [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод получения списка сообщений из почтового ящика Exchange Server. [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод получает основную информацию о сообщениях, например тему, идентификатор сообщения, от и до.

Чтобы получить полную информацию о сообщении, Aspose.Email.Exchange предоставляет [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) метод. Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) класс. [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) Затем класс предоставляет сведения о сообщении, такие как текст, заголовки и вложения.

{{% /alert %}}
## **Получение сообщений из почтового ящика сервера Exchange**
Чтобы получить сообщения из почтового ящика сервера Exchange, выполните следующие действия:

1. Создайте экземпляр типа [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Позвоните [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод получения [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Пройдите через [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) коллекция, которую можно получить [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) values.
1. Call [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) и сдай [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) в качестве параметра.

Следующий фрагмент кода подключается к почтовому ящику Exchange Server и загружает все сообщения.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}
