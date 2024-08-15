---
title: Read Outlook PST File and Get Folders and Subfolders Information
type: docs
weight: 110
url: /java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
---

{{% alert color="primary" %}} 

Aspose.Email for Java lets you read Microsoft Outlook PST files. You can load a PST file from disk or stream into an instance of the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class and get the information about its contents, for example, folders, subfolders, and messages.

{{% /alert %}} 

## **Load a PST File**

An Outlook PST file can be loaded into an instance of the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class. A code snippet for loading the PST file is given below:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Displaying Folders Information**

After loading the PST file into the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class, you can get the information about the file display name, root folder, subfolders and messages count. The following code snippet displays the name of a PST file, folders and number of messages in the folders:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Get user-defined folders only**

A PST/OST files may contain folders that were created by the user. Aspose.Email provides the ability to access only user-defined folders by using the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) property. You can set the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) property to **true** to get only user-defined folders. The following code snippet demonstrates the use of [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) to get user-defined folders.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Checking whether the folder is in a predefined folder**

When opening and inspecting the folders within a PST (Personal Storage Table) file, you can check whether each folder is a predefined folder type or a subfolder of a predefined folder type, and obtain the information about each folder.

The [FolderInfo.getPredefinedType(boolean getForTopLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) method is used to check whether the folder is from [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/). 

If 'getForTopLevelParent' param is true, method returns a StandardIpmFolder enum value for the top-level parent folder. This determines whether the current folder is a subfolder of a predefined folder. If 'getForTopLevelParent' param is false, it returns a StandardIpmFolder enum value for the current folder.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Display Name: " + folder.getDisplayName());

        // Determines whether the current folder is a predefined folder
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
        System.out.println("Is StandardIpmFolder?: " + answer);

        // Determines whether the current folder is a subfolder of a predefined folder
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
            System.out.println("Is subfolder from StandardIpmFolder parent?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Get or Add a standard RSS Feeds folder in a PST File**

Aspose.Email makes it possible to retrieve a reference to the predefined folder that holds RSS feeds. This could be useful if you want to programmatically access and manipulate the RSS feeds stored in an Outlook PST file. Give the value of RssFeeds to the [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/) enum.

The following code example shows how to get an RSS Feeds folder:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
And the code sample below demonstrates how to add an RSS Feeds folder:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Parse Searchable Folders**

A PST/OST may contain searchable folders in addition to the normal type of folders. Aspose.Email provides the [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) enumerator for specifying the messages from such search folders with [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) and [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--) methods.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Retrieve Parent Folder Information from MessageInfo**

The following code snippet shows you how to retrieve parent folder information from [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **PST file traversal API**

The traversal API allows extracting all PST items as far as possible, without throwing out exceptions, even if some data of the original file is corrupted.
The following steps show how to use this API.

Use [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) constructor and [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) method instead of fromFile method.

The constructor allows defining a callback method.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
    }
})) {
    //
}
```

Loading and traversal exceptions will be available through the callback method.

The [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```java
if (currentPst.load(inputStream))
```

This allows to open and traverse even corrupted PST files without throwing out exceptions. Both exceptions and corrupted items will be handled by the callback method.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
    }
})) {
    if (pst.load("test.pst")) {
        getAllMessages(pst, pst.getRootFolder());
    }
}

private static void getAllMessages(PersonalStorage pst, FolderInfo folder) {
    for (String messageEntryId : folder.enumerateMessagesEntryId()) {
        MapiMessage message = pst.extractMessage(messageEntryId);
    }
    for (FolderInfo subFolder : folder.getSubFolders()) {
        getAllMessages(pst, subFolder);
    }
}
```
