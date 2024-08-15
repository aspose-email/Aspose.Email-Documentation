---
title: "Поддержка команд и расширений IMAP IDLE"
url: /ru/java/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Поддержка команды IMAP Idle**

API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность открыть соединение с сервером и дождаться получения сообщения электронной почты. Это позволяет избежать повторного опроса сервера на предмет получения входящей электронной почты. В следующем фрагменте кода показано, как поддерживать команду IMAP Idle.

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

## **Поддержка расширений IMAP**

API Aspose.Email обеспечивает поддержку расширений IMAP. В настоящее время API поддерживает следующие расширения IMAP. Эти расширения IMAP поддерживаются не всеми серверами.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password");
try {
    // Set SecurityOptions
    client.setSecurityOptions(SecurityOptions.Auto);
    System.out.println(client.getIdSupported());

    ImapIdentificationInfo serverIdentificationInfo1 = client.introduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.introduceClient(ImapIdentificationInfo.getDefaultValue());

    // Display ImapIdentificationInfo properties
    System.out.println(serverIdentificationInfo1.toString() + serverIdentificationInfo2.toString());
    System.out.println(serverIdentificationInfo1.getName());
    System.out.println(serverIdentificationInfo1.getVendor());
    System.out.println(serverIdentificationInfo1.getSupportUrl());
    System.out.println(serverIdentificationInfo1.getVersion());
} finally {
    if (client != null)
        client.dispose();
}
~~~

### **Команда расширенного списка IMAP4**

В следующем фрагменте кода показано, как использовать команду IMAP4 extended list.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password");
try {
    ImapFolderInfoCollection folderInfoCol = client.listFolders("*");
    System.out.println("Extended List Supported: " + client.getExtendedListSupported());
    for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoCol) {
        if (folderInfo.getName().equals("[Gmail]/All Mail"))
            System.out.println("Has Children: " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Bin"))
            System.out.println("Bin has children? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Drafts"))
            System.out.println("Drafts has children? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Important"))
            System.out.println("Important has Children? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Sent Mail"))
            System.out.println("Sent Mail has Children? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Spam"))
            System.out.println("Spam has Children? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Starred"))
            System.out.println("Starred has Children? " + folderInfo.hasChildren());
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~
