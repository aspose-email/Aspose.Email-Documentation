---
title: Create New PST, Add Sub-folders and Messages
ArticleTitle: Create New PST, Add Sub-folders and Messages
type: docs
weight: 10
url: /java/create-new-pst-add-sub-folders-and-messages/
---


As well as parsing an existing PST file, Aspose.Email provides the means to create a PST file from scratch. This article demonstrates how to create an Outlook PST file and add a subfolder to it.

1. [Creating a new PST file](#creating-a-new-pst-file-and-add-subfolders).
1. [Changing Container class of a folder](#changing-a-folders-container-class).
1. [Add Bulk Messages with Improved Performance](#add-bulk-messages-with-improved-performance) 

Use the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class to create a PST file at some location on a local disk. To create a PST file from scratch:

1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Add a sub-folder at the root of the PST file by accessing the Root folder and then calling the [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-) method.

The following code snippet shows you how to create a PST file and add a subfolder called Inbox.

```java
// Create new PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Add new folder "Test"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Create PST with Size more than 2Gb using OutputStream**

Aspose.Email users can optimize PST internal cache using the PersonalStorage constructor:

- **blockSize** - The optimal block size to expand cache buffer(in bytes).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Reduce the message size and the size of the created PST file**

Aspose.Email offers the capability to compress the body content, which can help reduce the message size. This can be particularly useful when sending large messages or when dealing with limited bandwidth or storage constraints. For this purpose, the library provides the compression parameter included in the following methods:

- [MapiMessageItemBase.setBodyContent(String content, /*BodyContentType*/int contentType, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Sets the content of the body.
- [MapiMessageItemBase.setBodyRtf(String content, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Gets or sets the RTF formatted message text.

The code snippet below demonstrates how to use RTF Compression while setting the MAPI message body:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Create PersonalStorage based on SeekableByteChannel Stream**

Aspose.Email for Java makes it possible to work with Personal Storage (PST) files using java.nio.channels. It allows you create a PersonalStorage instance using a SeekableByteChannel stream. The following code snippet demonstrates how to create a PersonalStorage instance based on a FileChannel stream, add a subfolder named "messageFolder" to the root folder, and import messages from files in the "messageFolder" directory: 


```cs
try (RandomAccessFile raf = new RandomAccessFile("test.pst", "rw")) {
    FileChannel channel = raf.getChannel();
    try (PersonalStorage pst = PersonalStorage.create(channel, FileFormatVersion.Unicode)) {
        FolderInfo messageFolder = pst.getRootFolder().addSubFolder("messageFolder");

        for (File f : new File("messageFolder").listFiles()) {
            messageFolder.addMessage(MapiMessage.load(f.getAbsolutePath()));
        }
    }
}
```


## **Changing a Folder Container Class**

Sometimes it is necessary to change a folder class. A common example is where messages of different types (appointments, messages, etc.) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code snippet shows you how to change the container class of a folder in PST for this purpose.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Add Bulk Messages with Improved Performance**

Adding individual messages to a PST implies more I/O operations to disc and may slow down the performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. 
The [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) method allows you to add messages in bulk and can be used as in the following scenarios. In addition, the [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) event occurs when a message is added to the folder.

### **Add Messages from Another PST**

To add messages from another PST, use the [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) method that returns `Iterable<MapiMessage>`:

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

### **Add Messages from Directory**

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

