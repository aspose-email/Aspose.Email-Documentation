---
title: "Список сообщений с сервера Exchange с использованием WebDAV"
url: /ru/java/listing-messages-from-exchange-server-using-webdav/
weight: 60
type: docs
---

Список сообщений электронной почты в почтовом ящике Exchange можно получить, позвонив в [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод. Получите базовую информацию о сообщениях, такую как тема, от кого и идентификатор сообщения, используя [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method.

В этой статье показано, как подключиться к серверу Exchange и вывести список сообщений электронной почты в почтовом ящике напрямую или с помощью WebDAV. Далее показано, как перечислять сообщения из разных папок и как перечислять сообщения по идентификатору.
## **Список сообщений сервера Exchange**
Чтобы вывести список сообщений в почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Позвоните [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод и создайте коллекцию сообщений.
1. Просмотрите коллекцию и отобразите информацию о сообщениях.

Приведенный ниже фрагмент кода подключается к почтовому ящику Exchange и получает список сообщений из папки «Входящие».

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Список сообщений из разных папок**
В приведенных выше фрагментах кода перечислены все сообщения в папке «Входящие». Можно также получить список сообщений из других папок. [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) метод принимает URI папки в качестве параметра. Если URI папки действителен, вы можете получить список сообщений из этой папки.

Используйте URL-адрес папки ExchangeClient.getMailboxInfo () .xxx[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) свойство для получения URI разных папок. В остальном код такой же, как и при получении списка сообщений.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}
