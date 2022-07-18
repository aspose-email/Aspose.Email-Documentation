---
title: Read Outlook PST File and Get Folders and Subfolders Information
type: docs
weight: 110
url: /java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
---

{{% alert color="primary" %}} 

Aspose.Email for Java lets you read Microsoft Outlook PST files. You can load a PST file from disk or stream into an instance of the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class and get the information about its contents, for example, folders, subfolders, and messages.

{{% /alert %}} 
## **Load a PST File**
An Outlook PST file can be loaded into an instance of the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class. A code snippet for loading the PST file is given below:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}
## **Displaying Folders Information**
After loading the PST file into the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class, you can get the information about the file display name, root folder, subfolders and messages count. The following code snippet displays the name of a PST file, folders and number of messages in the folders:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}
## **Get user-defined folders only**
A PST/OST files may contain folders that were created by the user. Aspose.Email provides the ability to access only user-defined folders by using the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorageQueryBuilder#getOnlyFoldersCreatedByUser\(\)) property. You can set the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorageQueryBuilder#getOnlyFoldersCreatedByUser\(\)) property to **true** to get only user-defined folders. The following code snippet demonstrates the use of [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorageQueryBuilder#getOnlyFoldersCreatedByUser\(\)) to get user-defined folders.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}
## **Parse Searchable Folders**
A PST/OST may contain searchable folders in addition to the normal type of folders. Aspose.Email provides the [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/FolderKind) enumerator for specifying the messages from such search folders with [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateFolders\(\)) and [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#getSubFolders\(\)) methods.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}
## **Retrieve Parent Folder Information from MessageInfo**
The following code snippet shows you how to retrieve parent folder information from [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/MessageInfo).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}
