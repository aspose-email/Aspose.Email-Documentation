---
title: "Работа с флагами сообщений на сервере"
url: /ru/net/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Изменение флагов сообщений**

Вы можете изменить флаги сообщений, используя [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/) метод. Этот метод принимает два параметра.

1. Порядковый номер сообщения или его уникальный идентификатор.
2. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/).

Можно установить следующие флаги:

- [Answered](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/answered/)
- [Deleted](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/deleted/)
- [Draft](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/draft/)
- [Empty](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/empty/)
- [Flagged](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/flagged/)
- [IsRead](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/isread/)
- [Recent](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/recent/)

### **Настройка флагов сообщений**

В следующем фрагменте кода показано, как изменить флаги сообщений на сервере IMAP с помощью Aspose.Email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}

### **Удаление флагов сообщений**

Флаги сообщений также можно удалить с помощью [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/removemessageflags/#removemessageflags/) метод. Использование аналогично использованию [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/) метод. Он принимает порядковый номер или уникальный идентификатор сообщения и [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/). В следующем фрагменте кода показано, как удалить флаги сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}

## **Настройка собственных флагов**

Вы также можете установить собственные флаги для сообщения, используя [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API. IMapClient AddMessageFlags предоставляет возможность устанавливать собственные флаги для сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}
