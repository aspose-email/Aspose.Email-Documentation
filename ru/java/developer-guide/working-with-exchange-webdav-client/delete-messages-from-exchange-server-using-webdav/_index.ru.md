---
title: "Удаление сообщений из Exchange Server с использованием WebDav"
url: /ru/java/delete-messages-from-exchange-server-using-webdav/
weight: 20
type: docs
---

Вы можете удалить электронные сообщения из папки с помощью метода [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)). Он принимает уникальный URI сообщения в качестве параметра.

Пример кода ниже удаляет сообщение из папки Входящие. Для целей этого примера, код:

1. Читает сообщения из папки Входящие.
1. Обрабатывает сообщения на основе определенных критериев (в этом примере мы ищем ключевое слово в теме сообщения).
1. Удаляет сообщение.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}