---
title: "Soporte para el comando IMAP IDLE"
url: /es/java/support-for-imap-idle-command/
weight: 100
type: docs
---


Aspoe.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona la capacidad de abrir una conexión al servidor y esperar la llegada de un mensaje de correo electrónico. Esto permite evitar consultar al servidor una y otra vez por cualquier correo electrónico entrante. El siguiente fragmento de código muestra cómo soportar el comando IMAP Idle.

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