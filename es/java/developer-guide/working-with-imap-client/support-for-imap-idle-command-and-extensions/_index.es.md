---
title: "Soporte para comandos y extensiones IMAP IDLE"
url: /es/java/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Soporte para el comando IMAP Idle**

API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) ofrece la posibilidad de abrir una conexión con el servidor y esperar la llegada de un mensaje de correo electrónico. Esto permite evitar sondear el servidor una y otra vez para detectar cualquier correo electrónico entrante. El siguiente fragmento de código muestra cómo utilizar el comando IMAP Idle.

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

## **Soporte para extensiones IMAP**

La API Aspose.Email proporciona soporte para extensiones IMAP. Actualmente, la API admite las siguientes extensiones IMAP. Estas extensiones IMAP no son compatibles con todos los servidores.

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

### **Comando de lista extendida IMAP4**

El siguiente fragmento de código muestra cómo usar el comando de lista extendida IMAP4.

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
