---
title: Read Outlook for Mac OLM File and Get Folders and SubFolders Information
ArticleTitle: Read Outlook for Mac OLM File and Get Folders and SubFolders Information
type: docs
weight: 130
url: /java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
---

{{% alert color="primary" %}} 

Aspose.Email for Java allows you to read Outlook for Mac OLM files. You can load an OLM file from disk into an instance of the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) class and get the information about its contents, for example, folders, subfolders, and messages.

{{% /alert %}} 

## **Open OLM format files**

OLM format files can be opened in two ways:

- using constructor
- using static FromFile method

There are differences in behavior between these methods. See section below.

### **Open files by constructor**

To open a file, call constructor of the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) class and pass full file name or stream as an argument to it:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Open files using static method FromFile**

To open a file, use static method [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) and pass full file name as an argument to it:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```
### **Open files using static method FromStream**

To open a file using static method [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), pass a stream name as an argument to it:


## **Read OLM file**

The following code snippet shows you how to load the OLM file and get its content.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Get folders**

To retrieve folders from an OLM (Outlook for Mac) file, load it with the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) class first, and then use one of the following methods depending on your needs:

- [getFolder(String name, boolean ignoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Gets the folder by name.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Gets the folder hierarchy/collection of folders.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Gets the folder hierarchy.

The code sample below will show you how to get a folder from an OLM file:

```java
// Get the folder by name
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
When using the [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) method to open an OLM file, the [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) will return null. In this case, call the [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) method explicitly to retrieve the list of directories in the OLM file.


### **Get Folder Path**

You may also get the folder path of folders in the OML file. Aspose.Email provides [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) property which returns the folder path. The following code snippet demonstrates the use of [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) property to get the folder paths in the OML file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Count the number of items in the folder**

You may also count the number of items in the folder. Aspose.Email provides [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) property which returns the number of items in the folder. The following code snippet demonstrates the use of [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) property to get the number of items in the folders of the OML file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Enumerate Messages from a given Folder**

Aspose.Email provides the API to work with OLM storages and extract messages from a given folder. The [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) and [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) classes represent brief information about a folder and a message in the storage respectively. The [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) class provides the following methods:

- **OlmFolder.getSubFolder**(String subfolderName, boolean ignoreCase) - Gets the subfolder by name.

- **OlmFolder.enumerateMapiMessages()** - Exposes the enumerator, which supports an iteration of MapiMessages in the current folder.

- **OlmFolder.enumerateMessages()** - Exposes the enumerator, which supports an iteration of OlmMessageInfo's in the current folder.

- **OlmFolder.enumerateMessages**(int startIndex, int count) - Exposes the enumerator, which supports an iteration of OlmMessageInfo's within a given range.

- **OlmFolder.enumerateMessages**(MailQuery query) - Exposes the enumerator, which supports an iteration of OlmMessageInfo's by search criteria.

The code samples below will demonstrate the use of these methods:

```java
 // Enumerates all messages in a given folder

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates a range of messages in a given folder

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   int startIndex = 10;

   int count = 100;

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(startIndex, count)) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates messages by search criteria

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

    MailQueryBuilder mailQueryBuilder = new MailQueryBuilder();

    mailQueryBuilder.getSubject().contains("invitation");

    mailQueryBuilder.getFrom().contains("Mark");

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(mailQueryBuilder.getQuery())) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates all messages and the extraction of some of them

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

       if (messageInfo.hasAttachments()) {

            MapiMessage msg = olm.extractMapiMessage(messageInfo);

       }

   }

} finally {

    olm.dispose();

}
```
## **Extract Messages from OLM by Identifiers**

Sometimes it is required to extract selected messages by identifiers. For example, your application stores identifiers in a database and extracts a message on demand. This is the efficient way to avoid traversing through the entire storage each time to find a specific message to extract. To implement this feature for OLM files, Aspose.Email provides the following methods and classes:

- [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) property of the [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) class - Gets the message entry identifier.
- overloaded [extractMapiMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) method of the [OlmStorage]() class - Gets the message from OLM.

The code sample below demonstrates how to extract messages from OLM by identifiers:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Note:** The message ID is unique within the storage file. IDs are created by Aspose.Email and cannot be used in other third-party OLM processing libs or apps.


## **Extract OLM Items from Corrupted Files**

Aspose.Email provides a traversal API which allows extracting all OLM items as far as possible, without throwing out exceptions, even if some data of the original file is corrupted.

Use the [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) constructor and the [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) method instead of the [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) method.

The constructor allows defining a callback method.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
});
```
Loading and traversal exceptions will be available through the callback method.

The load method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
};
try (OlmStorage olm = new OlmStorage(exceptionsCallback)) {
    if (olm.load(fileName)) {
        List<OlmFolder> folderHierarchy = olm.getFolders();
        extractItems(olm, folderHierarchy);
    }
}

private static void extractItems(OlmStorage olm, List<OlmFolder> folders) {
    for (OlmFolder folder : folders) {
        if (folder.hasMessages()) {
            System.out.println(folder);

            for (MapiMessage msg : olm.enumerateMessages(folder)) {
                System.out.println(msg.getSubject());
            }
        }

        if (folder.getSubFolders().size() > 0) {
            extractItems(olm, folder.getSubFolders());
        }
    }
}
```
## **Get Message Modified Date**

The [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) property allows you to get the message modified date.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```
