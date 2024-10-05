---
title: "Работа с папками на WebDav"
url: /ru/java/working-with-folders-on-webdav/
weight: 130
type: docs
---


## **Список всех папок с сервера**
Aspose.Email API предоставляет возможность подключения к Exchange Server и получения списка всех папок и под-папок. Вы также можете рекурсивно получить все под-папки из каждой папки. Эта статья показывает, как получить все под-папки с сервера Exchange и извлечь папки с пагинацией.
### **Использование WebDav**
Следующий фрагмент кода демонстрирует, как получить список папок с сервера Exchange.


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