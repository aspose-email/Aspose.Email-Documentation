---
title: "Soporte para el comando IMAP IDLE"
url: /es/java/support-for-imap-idle-command/
weight: 100
type: docs
---


API de correo electrónico Aspoe.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) ofrece la posibilidad de abrir una conexión con el servidor y esperar la llegada de un mensaje de correo electrónico. Esto permite evitar sondear el servidor una y otra vez para detectar cualquier correo electrónico entrante. El siguiente fragmento de código muestra cómo utilizar el comando IMAP Idle.

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
