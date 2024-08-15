---
title: "Список серверных расширений с помощью Pop3Client"
url: /ru/python-net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---

## **Список серверных расширений с помощью Pop3Client**
Pop3Client от Aspose.Email позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. Метод getCapabilities () возвращает поддерживаемые типы расширений в виде строкового массива.
### **Получение серверных расширений**
В следующем примере кода показано получение серверных расширений с помощью IMapClient для сервера Gmail.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}
