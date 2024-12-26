---
title: Support for IMAP IDLE Command And Extensions
ArticleTitle: Support for IMAP IDLE Command And Extensions
type: docs
weight: 110
url: /java/support-for-imap-idle-command-and-extensions/
---


## **Support for IMAP Idle Command**

Aspose.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides the capability to open a connection to the server and wait for the arrival of an email message. This allows avoiding polling the server again and again for any incoming email. The following code snippet shows you how to Support for IMAP Idle Command.

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

## **Support for IMAP Extensions**

Aspose.Email API provides support for IMAP extensions. The following IMAP extensions are supported by the API at present. These IMAP extensions are not supported by all servers.

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

### **IMAP4 Extended List Command**

The following code snippet shows you how to use IMAP4 extended list command.

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
