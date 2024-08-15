---
title: "Список серверных расширений IMAP"
url: /ru/net/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) метод возвращает поддерживаемые типы расширений в виде строкового массива. В следующем фрагменте кода показано, как извлекать расширения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}
