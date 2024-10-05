---
title: "Сохранение сообщений из почтового ящика Exchange Server с использованием WebDav"
url: /ru/java/save-messages-from-exchange-server-mailbox-using-webdav/
weight: 90
type: docs
---

В этой статье показано, как получить сообщения из почтового ящика Exchange Server и сохранить их на диск в форматах EML и MSG.

## **Сохранение сообщений из почтового ящика Exchange Server в формат EML**
Чтобы получить сообщения и сохранить в формате EML:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Вызовите метод [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)), чтобы получить экземпляр коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection).
1. Пройдите по коллекции [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection), чтобы получить уникальный URI для каждого сообщения.
1. Вызовите метод [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) и передайте уникальный URI в качестве параметра.
1. Укажите метод [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) с путем, где вы хотите сохранить файл.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Сохранение сообщений в OutputStream**
Вместо сохранения EML файлов на диск можно сохранить их в OutputStream. Это полезно, когда вы хотите сохранить поток в какое-либо место хранения, например, в базу данных. Как только поток будет сохранен в базу данных, вы можете загрузить файл EML в класс [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).

Приведенные ниже фрагменты кода сохраняют сообщения из почтового ящика Exchange Server в память.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Сохранение сообщений в формате MSG**
Метод [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) может напрямую сохранять сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите метод [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)), который возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Затем вызовите метод [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)), чтобы сохранить сообщение в формате MSG.

Приведенный ниже фрагмент кода получает сообщения из почтового ящика Exchange Server и сохраняет их в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}