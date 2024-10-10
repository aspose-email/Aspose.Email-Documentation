---
title: "Поддержка команды IMAP IDLE"
url: /ru/java/support-for-imap-idle-command/
weight: 100
type: docs
---

Aspoe.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность открыть соединение с сервером и ждать поступления email сообщения. Это позволяет избежать повторных опросов сервера в поисках входящей почты. Следующий фрагмент кода показывает, как поддерживать команду IMAP Idle.

```Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.domain.com", "username", "password");

client.startMonitoring(new ImapMonitoringEventHandler() {
    public void invoke(Object sender, ImapMonitoringEventArgs e) {
        System.out.println(e.getNewMessages().length);
        System.out.println(e.getDeletedMessages().length);
    }
});
client.stopMonitoring("Inbox");
```

