---
title: "Сохранение сообщений из почтового ящика сервера Exchange с помощью WebDAV"
url: /ru/java/save-messages-from-exchange-server-mailbox-using-webdav/
weight: 90
type: docs
---

В этой статье показано, как получать сообщения из почтового ящика Exchange Server и сохранять их на диск в форматах EML и MSG.
## **Сохранение сообщений из почтового ящика сервера Exchange в EML**
Чтобы получать сообщения и сохранять их в формате EML, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Позвоните [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод получения экземпляра [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) collection.
1. Пройдите через [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) коллекция для получения уникального URI для каждого сообщения.
1. Позвоните [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) метод и передайте уникальный URI в качестве параметра.
1. Предоставьте [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) метод с указанием пути к месту сохранения файла.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Сохранение сообщений в OutputStream**
Вместо сохранения файлов EML на диск их можно сохранить в OutputStream. Это удобно, если вы хотите сохранить поток в каком-либо месте хранения, например в базе данных. Как только поток будет сохранен в базе данных, вы можете перезагрузить файл EML в [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.

Приведенные ниже фрагменты кода сохраняют сообщения из почтового ящика Exchange Server в поток памяти.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Сохранение сообщений в формате MSG**
The [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) метод может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) метод, который возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. Затем позвоните [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) метод сохранения сообщения в MSG.

Приведенный ниже фрагмент кода позволяет получать сообщения из почтового ящика Exchange Server и сохранять их в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}
