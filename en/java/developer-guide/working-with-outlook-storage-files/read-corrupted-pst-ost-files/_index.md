---
title: Read corrupted PST/OST files
type: docs
weight: 112
url: /java/read-corrupted-pst-ost-files/
---

## **Read corrupted PST/OST files**

Sometimes it may not be possible to read the PST/OST due to some issues. For example, some data blocks may be corrupted. In such cases, exceptions usually arise when calling the [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--), etc. methods. But individual messages or folders may remain undamaged in the storage.

Aspose.Email users can find item identifiers in a hierarchical manner. Further, you can extract items by identifiers. For this purpose, the library offers the following methods:

- [PersonalStorage.findMessages(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - finds the identifiers of messages for the folder.
- [PersonalStorage.findSubfolders(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - finds the identifiers of subfolders for the folder.

**Note**, that despite the advantages, there are corrupted storages that cannot be read even using these methods.

The following code snippet demonstrates the use of these methods to read corrupted PST/OST files:

```java
try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    exploreCorruptedPst(pst, pst.getRootFolder().getEntryIdString());
}

public static void exploreCorruptedPst(PersonalStorage pst, String rootFolderId) {
    Iterable<String> messageIdList = pst.findMessages(rootFolderId);

    for (String messageId : messageIdList) {
        try {
            MapiMessage msg = pst.extractMessage(messageId);
            System.out.println("- " + msg.getSubject());
        } catch (Exception e) {
            System.out.println("Message reading error. Entry id: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Message reading error. Entry id: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Extract PST Items from Corrupted Files**

The traversal API allows extracting all PST items as far as possible, without throwing out exceptions, even if some data of the original file is corrupted.

Use the [PersonalStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) constructor and the [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) method instead of the [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-) method.

The constructor allows defining a callback method.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Loading and traversal exceptions will be available through the callback method.

The load method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```java
if (currentPst.load(inputStream))
```
The following code sample shows how to implement PST file traversal API into a project:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Exception handling  code. */
        }
    };

    try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) {
        if (pst.load("test.pst")) {
            getAllMessages(pst, pst.getRootFolder());
        }
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