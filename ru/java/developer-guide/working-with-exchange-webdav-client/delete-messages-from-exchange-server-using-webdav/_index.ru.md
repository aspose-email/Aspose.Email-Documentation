---
title: "Удаление сообщений с сервера Exchange с помощью WebDAV"
url: /ru/java/delete-messages-from-exchange-server-using-webdav/
weight: 20
type: docs
---

Вы можете удалить сообщения электронной почты из папки с помощью [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)) метод. В качестве параметра он принимает уникальный URI сообщения.

Приведенный ниже пример кода удаляет сообщение из папки «Входящие». Для целей этого примера код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывайте сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удалите сообщение.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}
