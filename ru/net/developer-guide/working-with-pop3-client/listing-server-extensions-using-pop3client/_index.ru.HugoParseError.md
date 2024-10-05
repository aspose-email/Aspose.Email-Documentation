---
title: Получение расширений сервера с использованием Pop3Client
type: docs
weight: 30
url: /net/listing-server-extensions-using-pop3client/
---

Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) позволяет вам получать расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для данной функциональности. Метод [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) возвращает поддерживаемые типы расширений в форме массива строк.

## **Получение расширений сервера**

Следующий пример кода демонстрирует получение расширений сервера, используя ImapClient для сервера Gmail.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}