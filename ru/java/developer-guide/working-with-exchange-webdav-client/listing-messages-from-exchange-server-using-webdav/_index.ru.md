---
title: "Список сообщений из Exchange Server с использованием WebDav"
url: /ru/java/listing-messages-from-exchange-server-using-webdav/
weight: 60
type: docs
---

Список электронных сообщений в почтовом ящике Exchange можно получить, вызвав метод [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)). Получите основную информацию о сообщениях, такую как тема, отправитель, получатель и ID сообщения, используя метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)).

В этой статье показано, как подключиться к Exchange Server и вывести электронные письма в почтовом ящике напрямую или с использованием WebDav. Также показано, как перечислять сообщения из разных папок и как выводить сообщения по ID.
## **Список сообщений Exchange Server**
Чтобы перечислить сообщения в почтовом ящике Exchange:

1. Создайте экземпляр класса [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Вызовите метод [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) и создайте коллекцию сообщений.
1. Переберите коллекцию и отобразите информацию о сообщениях.

Приведенный ниже фрагмент кода подключается к почтовому ящику Exchange и получает список сообщений из папки Входящие.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Перечисление сообщений из разных папок**
Приведенные выше фрагменты кода перечисляют все сообщения в папке Входящие. Возможно также получить список сообщений из других папок. Метод [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) принимает URI папки в качестве параметра. Пока URI папки действителен, вы можете получить список сообщений из этой папки.

Используйте свойство ExchangeClient.getMailboxInfo().xxxFolderUri[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) для получения URI различных папок. Остальной код такой же, как и для получения списка сообщений.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}