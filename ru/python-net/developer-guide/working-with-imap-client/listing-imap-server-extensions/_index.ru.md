---
title: "Список серверных расширений IMAP"
url: /ru/python-net/listing-imap-server-extensions/
weight: 40
type: docs
---


## **Список расширений для серверов**
IMapClient от Aspose.Email позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. Метод getCapabilities () возвращает поддерживаемые типы расширений в виде строкового массива. В следующем фрагменте кода показано, как извлекать расширения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}
