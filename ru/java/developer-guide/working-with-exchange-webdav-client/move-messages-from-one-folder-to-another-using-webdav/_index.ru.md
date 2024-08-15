---
title: "Перемещение сообщений из одной папки в другую с помощью WebDAV"
url: /ru/java/move-messages-from-one-folder-to-another-using-webdav/
weight: 70
type: docs
---

Вы можете перемещать сообщения электронной почты из одной папки в другую с помощью [ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)) метод. Он принимает следующие параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI целевой папки.
## **Перемещение сообщений между папками**
Приведенный ниже пример кода, который перемещает сообщение в почтовом ящике из папки «Входящие» в папку «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, удовлетворяющие заданному условию, в папку Processed.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}
