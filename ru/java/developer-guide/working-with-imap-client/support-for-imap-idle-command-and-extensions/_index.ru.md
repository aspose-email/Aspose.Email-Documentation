---
title: "Поддержка команды IMAP IDLE и дополнительных функций"
url: /ru/java/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Поддержка команды IMAP Idle**

Aspose.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность установить соединение с сервером и ожидать поступления сообщения электронной почты. Это позволяет избежать постоянного опроса сервера для получения входящей почты. Следующий фрагмент кода показывает, как поддерживать команду IMAP Idle.

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

## **Поддержка IMAP расширений**

Aspose.Email API предоставляет поддержку IMAP расширений. В настоящее время API поддерживает следующие IMAP расширения. Эти IMAP расширения не поддерживаются всеми серверами.

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

### **Команда IMAP4 Extended List**

Следующий фрагмент кода показывает, как использовать команду IMAP4 extended list.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password");
try {
    ImapFolderInfoCollection folderInfoCol = client.listFolders("*");
    System.out.println("Расширенный список поддерживается: " + client.getExtendedListSupported());
    for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoCol) {
        if (folderInfo.getName().equals("[Gmail]/Все письма"))
            System.out.println("Есть дочерние элементы: " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Корзина"))
            System.out.println("Корзина имеет дочерние элементы? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Черновики"))
            System.out.println("Черновики имеют дочерние элементы? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Важные"))
            System.out.println("Важные имеют дочерние элементы? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Отправленные"))
            System.out.println("Отправленные имеют дочерние элементы? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Спам"))
            System.out.println("Спам имеет дочерние элементы? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Звёздные"))
            System.out.println("Звёздные имеют дочерние элементы? " + folderInfo.hasChildren());
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~