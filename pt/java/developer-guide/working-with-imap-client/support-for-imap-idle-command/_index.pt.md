---
title: "Suporte para o Comando IMAP IDLE"
url: /pt/java/support-for-imap-idle-command/
weight: 100
type: docs
---

A API Aspoe.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece a capacidade de abrir uma conexão com o servidor e aguardar a chegada de uma mensagem de email. Isso permite evitar a verificação constante do servidor em busca de novos emails. O seguinte trecho de código mostra como suportar o comando IMAP Idle.

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