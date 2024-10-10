---
title: "Перемещение сообщений из одной папки в другую с помощью WebDav"
url: /ru/java/move-messages-from-one-folder-to-another-using-webdav/
weight: 70
type: docs
---

Вы можете перемещать электронные сообщения из одной папки в другую с помощью метода [ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)). Он принимает следующие параметры:

- Уникальный URI сообщения, которое необходимо переместить.
- Уникальный URI целевой папки.
## **Перемещение сообщений между папками**
Пример кода ниже перемещает сообщение в почтовом ящике из папки Входящие в папку с именем Обработанные. В этом примере приложение:

1. Читает сообщения из папки Входящие.
1. Обрабатывает некоторые сообщения на основе определенных критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, которые соответствуют заданному условию, в папку Обработанные.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}