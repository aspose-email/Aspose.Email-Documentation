---
title: "Перечисление расширений сервера с использованием Pop3Client"
url: /ru/python-net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---

## **Перечисление расширений сервера с использованием Pop3Client**
Pop3Client от Aspose.Email позволяет получить расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для конкретной функции. Метод GetCapabilities() возвращает поддерживаемые типы расширений в виде массива строк.
### **Получение расширений сервера**
Следующий пример кода демонстрирует получение расширений сервера с использованием ImapClient для сервера Gmail.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}