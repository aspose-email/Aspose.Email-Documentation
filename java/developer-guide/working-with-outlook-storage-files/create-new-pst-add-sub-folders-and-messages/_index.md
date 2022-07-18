---
title: Create New PST, Add Sub-folders and Messages
type: docs
weight: 10
url: /java/create-new-pst-add-sub-folders-and-messages/
---


As well as parsing an existing PST file, Aspose.Email provides the means to create a PST file from scratch. This article demonstrates how to create an Outlook PST file and add a subfolder to it.


1. [Creating a new PST file](#creating-a-new-pst-file-and-add-subfolders).
1. [Changing Container class of a folder](#changing-a-folders-container-class).
1. [Add Bulk Messages with Improved Performance](#add-bulk-messages-with-improved-performance) 


Use the [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) class to create a PST file at some location on a local disk. To create a PST file from scratch:

1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#create\(java.io.OutputStream,%20int\)) method.
1. Add a sub-folder at the root of the PST file by accessing the Root folder and then calling the [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addSubFolder\(java.lang.String\)) method.

The following code snippet shows you how to create a PST file and add a subfolder called Inbox.

```java
// Create new PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Add new folder "Test"
    pst.getRootFolder().addSubFolder("Inbox");
}
```

## **Changing a Folder's Container Class**
Sometimes it is necessary to change a folder's folder class. A common example is where messages of different types (appointments, messages, etc.) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code snippet shows you how to change the container class of a folder in PST for this purpose.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Add Bulk Messages with Improved Performance**

Adding individual messages to a PST implies more I/O operations to disc and may slow down the performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. 
The [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMessages\(java.lang.Iterable\)) method allows you to add messages in bulk and can be used as in the following scenarios. In addition, the [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#MessageAdded) event occurs when a message is added to the folder.

### Add Messages from Another PST

To add messages from another PST, use the [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateMapiMessages\(\)) method that returns `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Get the folder by name
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Handles the MessageAdded event.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Added: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### Add Messages from Directory

To add messages from directory, create the `getMessages(String pathToDir)` method that returns `Iterable<MapiMessage>`:

```java
// Read messages from directory.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Handles the MessageAdded event.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Added: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```

