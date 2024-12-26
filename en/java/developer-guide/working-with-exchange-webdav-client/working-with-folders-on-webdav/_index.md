---
title: Working with Folders on WebDav
ArticleTitle: Working with Folders on WebDav
type: docs
weight: 130
url: /java/working-with-folders-on-webdav/
---


## **Listing all Folders from Server**
Aspose.Email API provides the capability to connect to the Exchange Server and list all the folders and sub-folders. You can also retrieve all the sub-folders from each folder recursively. This article shows how to retrieve all the sub-folders from the Exchange server and retrieve folders with pagination.
### **Using WebDav**
The following code snippet shows you how to List folders from Exchange Server.


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
