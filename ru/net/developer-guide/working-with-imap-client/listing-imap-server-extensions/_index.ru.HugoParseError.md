---
title: Список расширений IMAP сервера
type: docs
weight: 80
url: /net/listing-imap-server-extensions/
---

Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) позволяет вам получить расширения сервера, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для данной функциональности. Метод [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) возвращает поддерживаемые типы расширений в виде массива строк. Следующий фрагмент кода показывает, как получить расширения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}