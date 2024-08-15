---
title: "Trabajando con carpetas en WebDAV"
url: /es/java/working-with-folders-on-webdav/
weight: 130
type: docs
---


## **Listar todas las carpetas del servidor**
La API Aspose.Email ofrece la capacidad de conectarse al servidor Exchange y enumerar todas las carpetas y subcarpetas. También puede recuperar todas las subcarpetas de cada carpeta de forma recursiva. En este artículo se muestra cómo recuperar todas las subcarpetas del servidor de Exchange y cómo recuperar las carpetas con paginación.
### **Uso de WebDAV**
El siguiente fragmento de código muestra cómo enumerar carpetas de Exchange Server.


~~~Java
public static void run() {
    try {
        ExchangeClient client = new ExchangeClient("http://ex07sp1/exchange/Administrator", "user", "pwd", "domain");
        System.out.println("Downloading all messages from Inbox....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listSubFolders(client, folderInfo);
        }

        System.out.println("All messages downloaded.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

private static void listSubFolders(ExchangeClient client, ExchangeFolderInfo folderInfo) {
    System.out.println(folderInfo.getDisplayName());
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        for (ExchangeFolderInfo subfolderInfo : folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }
}
~~~