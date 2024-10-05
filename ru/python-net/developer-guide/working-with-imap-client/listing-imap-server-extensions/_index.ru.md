---
title: "Перечисление расширений сервера IMAP"
url: /ru/python-net/listing-imap-server-extensions/
weight: 40
type: docs
---


## **Перечисление расширений сервера**
ImapClient от Aspose.Email позволяет извлекать расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для этой конкретной функции. Метод GetCapabilities() возвращает поддерживаемые типы расширений в виде массива строк. Следующий фрагмент кода показывает, как извлечь расширения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}