---
title: "Список серверных расширений с помощью Pop3Client"
url: /ru/net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) метод возвращает поддерживаемые типы расширений в виде строкового массива.

## **Получение серверных расширений**

В следующем примере кода показано получение серверных расширений с помощью IMapClient для сервера Gmail.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}
