---
title: Support for IMAP IDLE Command
ArticleTitle: Support for IMAP IDLE Command
type: docs
weight: 100
url: /java/support-for-imap-idle-command/
---


Aspoe.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides the capability to open a connection to the server and wait for the arrival of an email message. This allows avoiding polling the server again and again for any incoming email. The following code snippet shows you how to Support for IMAP Idle Command.

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
