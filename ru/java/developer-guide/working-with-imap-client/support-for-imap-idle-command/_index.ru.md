---
title: "Поддержка команды IMAP IDLE"
url: /ru/java/support-for-imap-idle-command/
weight: 100
type: docs
---


API Aspoe.Электронная почта [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность открыть соединение с сервером и дождаться получения сообщения электронной почты. Это позволяет избежать повторного опроса сервера на предмет получения входящей электронной почты. В следующем фрагменте кода показано, как поддерживать команду IMAP Idle.

~~~Java
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
~~~
