---
title: Работа с флагами сообщений на сервере
type: docs
weight: 30
url: /net/working-with-message-flags-on-server/
---


## **Изменение флагов сообщения**

Вы можете изменить флаги сообщения, используя метод [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Этот метод принимает два параметра.

1. Порядковый номер сообщения или его уникальный идентификатор.
2. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/).

Следующие флаги могут быть установлены:

- [Answered](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/answered/)
- [Deleted](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/deleted/)
- [Draft](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/draft/)
- [Empty](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/empty/)
- [Flagged](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/flagged/)
- [IsRead](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/isread/)
- [Recent](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/recent/)

### **Установка флагов сообщения**

Следующий фрагмент кода показывает, как изменить флаги сообщения на IMAP-сервере с помощью Aspose.Email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}

### **Удаление флагов сообщения**

Флаги сообщения также могут быть удалены с помощью метода [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/removemessageflags/#removemessageflags/). Использование этого метода аналогично методу [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Он принимает порядковый номер или уникальный идентификатор сообщения и [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/). Следующий фрагмент кода показывает, как удалить флаги сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}

## **Установка пользовательских флагов**

Вы также можете установить пользовательские флаги для сообщения, используя [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API. Метод ImapClient AddMessageFlags предоставляет возможность устанавливать пользовательские флаги на сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}