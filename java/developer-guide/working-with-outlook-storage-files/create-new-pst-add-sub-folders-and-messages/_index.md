---
title: Create New PST, Add Sub-folders and Messages
type: docs
weight: 10
url: /java/create-new-pst-add-sub-folders-and-messages/
---

Apart from parsing an existing PST, Aspose.Email also provides the means to create a PST file from scratch. This article shows how to create a Microsoft Outlook PST file and add a sub-folder to it. It uses the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class to create the PST on disk.

Below are the steps to create PST from scratch:

1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#create\(java.io.OutputStream,%20int\)) method.
1. Add a sub-folder at the PST root by accessing the Root folder and calling the [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addSubFolder\(java.lang.String\)) method.
1. Add a message to the newly created folder by calling [addMessage](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMessage\(com.aspose.email.MapiMessage\)) and passing a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) as a parameter.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-CreateNewPST-.java" >}}
## **Change a Folder's Container Class**
Sometimes it is necessary to change a folder's container class. A common example is where messages of different types (appointments, messages, for example) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code sample shows how to change the container class of a folder in PST for this purpose.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ChangeAFoldersContainerClass-.java" >}}
## **Add Bulk Messages with Improved Performance**
Adding individual messages to a PST implies more I/O operations to disc and may slow down the performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. The [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMessages\(java.lang.Iterable\)) method allows you to add messages in bulk and can be used as in the following scenarios. In addition, the [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#MessageAdded) event occurs when a message is added to the folder.
## **Add Messages from Another PST**
To add messages from another PST, use the [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateMapiMessages\(\)) method that returns IEnumerable<[MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage)>:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddBulkMessagesWithImprovedPerformance-BulkAddFromAnotherPst.java" >}}
## **Adding Bulk Messages from Disc**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddBulkMessagesWithImprovedPerformance-AddMessagesInBulkMode.java" >}}
## **Example Code for IEnumerable Implementation for Adding Messages from Files in a Directory**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-MapiMessageCollection-.java" >}}
