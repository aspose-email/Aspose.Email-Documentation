---
title: Working with Messages in a PST File
type: docs
weight: 30
url: /java/working-with-messages-in-a-pst-file/
---


## **Adding Messages to PST Files**
[Create a New PST File and Add Subfolders](/email/java/create-new-pst-add-sub-folders-and-messages) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add messages to subfolders of a PST file that you have created or loaded. This article adds two messages from disk to the Inbox subfolder of a PST. Use the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) and [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo) classes to add messages to PST files. To add messages to a PST file's Inbox folder:

1. Create an instance of the FolderInfo class and load it with the contents of the Inbox folder.
1. Add messages from disk to the Inbox folder by calling the [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMessages\(java.lang.Iterable\)) method. The [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo) class exposes the [addMessages](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMessages\(java.lang.Iterable\)) method that enables to add large number of messages to the folder, reducing I/O operations to disc and improving performance. A complete example can be found below, in [Adding Bulk Messages](#adding-bulk-messages).

The code snippets below shows how to add messages to a PST subfolder called Inbox.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create new PST
PersonalStorage personalStorage = PersonalStorage.create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.getRootFolder().addSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.addMessage(MapiMessage.fromFile(dataDir + "MapiMsgWithPoll.msg"));
~~~
### **Adding Bulk Messages**
Adding individual messages to a PST implies more I/O operations to disc and hence may slow down performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. The addMessages(Iterable<MapiMessage> messages) method allows you to define a range of message be added to the PST for improved performance and can be used as in the following scenarios. In addition, the MessageAdded event occurs when a message is added to the folder.
### **Loading Messages from Disc**
The following code snippet shows you how to loading messages from disc.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void addMessagesInBulkMode(String fileName, String msgFolderName) {
    try (PersonalStorage personalStorage = PersonalStorage.fromFile(fileName)) {
        FolderInfo folder = personalStorage.getRootFolder().getSubFolder("myInbox");
        folder.MessageAdded.add(new MessageAddedEventHandler() {
            public void invoke(Object sender, MessageAddedEventArgs e) {
                onMessageAdded(sender, e);
            }
        });
        folder.addMessages(new MapiMessageCollection(msgFolderName));
    }
}

static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~
### **Iterable Implementation**
The following code snippet shows you how to Iterable Implementation.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public class MapiMessageCollection implements Iterable<MapiMessage> {

    private final File folder;

    public MapiMessageCollection(String folder) {
        this.folder = new File(folder);
    }

    public Iterator<MapiMessage> iterator() {
        return new MapiMessageIterator(folder.listFiles());
    }
}

public class MapiMessageIterator implements Iterator<MapiMessage> {

    private Queue<String> queue = new LinkedList<String>();

    public MapiMessageIterator(File[] listOfFiles) {
        for (File file : listOfFiles) {
            queue.offer(file.getAbsolutePath());
        }
    }

    public boolean hasNext() {
        return !queue.isEmpty();
    }

    public MapiMessage next() {
        return MapiMessage.fromFile(queue.poll());
    }
}
~~~
### **Adding Messages from Other PST**
For adding messages from the another PST, use the [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#enumerateMapiMessages\(\)) method that returns Iterable<MapiMessage>. The following code snippet shows you how to add messages from other PST.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void bulkAddFromAnotherPst(String source) {
    // The path to the File directory.
    String dataDir = "data/";

    try (PersonalStorage pst = PersonalStorage.fromFile(source, false)) {
        try (PersonalStorage pstDest = PersonalStorage.fromFile(dataDir + "PersonalStorageFile1.pst")) {
            // Get the folder by name
            FolderInfo folderInfo = pst.getRootFolder().getSubFolder("Contacts");
            MessageInfoCollection ms = folderInfo.getContents();

            // Get the folder by name
            FolderInfo f = pstDest.getRootFolder().getSubFolder("myInbox");
            f.MessageAdded.add(new MessageAddedEventHandler() {
                public void invoke(Object sender, MessageAddedEventArgs e) {
                    onMessageAdded(sender, e);
                }
            });
            f.addMessages(folderInfo.enumerateMapiMessages());
            FolderInfo fi = pstDest.getRootFolder().getSubFolder("myInbox");
            MessageInfoCollection msgs = fi.getContents();
        }
    }
}

// Handles the MessageAdded event.
static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~
## **Get Messages Information from an Outlook PST File**
In [Read Outlook PST File and Get Folders and Subfolders Information](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/), we discussed loading an Outlook PST file and browse its folders to get the folder names and the number of messages in them. This article explains how to read all the folders and subfolders in the PST file and display the information about messages, for example, subject, sender, and recipients. The [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#getContents\(\)) method is used to display [brief message information](https://reference.aspose.com/email/java/com.aspose.email/MessageInfo) like subject, sender, recipients.
In terms of performance, this is the most suitable option for obtaining primary information about messages. To [extract](#extracting-messages-form-pst-files) complete message data, the [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(com.aspose.email.MessageInfo\)) method is provided.
The Outlook PST file may contain nested folders. To get message information from these, as well as the top-level folders, use a recursive method to read all the folders. The following code snippet shows you how to reads an Outlook PST file and display the folder and message contents recursively.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {

        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.fromFile(path);

        // Get the Display Format of the PST file
        System.out.println("Display Format: " + personalStorage.getFormat());

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.getRootFolder();

        // Call the recursive method to display the folder contents
        displayFolderContents(folderInfo, personalStorage);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void displayFolderContents(FolderInfo folderInfo, PersonalStorage pst) {
    // Display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Subject: " + messageInfo.getSubject());
        System.out.println("Sender: " + messageInfo.getSenderRepresentativeName());
        System.out.println("Recipients: " + messageInfo.getDisplayTo());
        System.out.println("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            displayFolderContents(subfolderInfo, pst);
        }
    }
}
~~~
## **Extracting Messages Form PST Files**
This article shows how to read Microsoft Outlook PST files and [extract messages](#extracting-messages-form-pst-files). The messages are then saved to disk in MSG format. The article also shows how to [extract a specific number of messages](#extracting-n-number-of-messages-from-a-pst-file) from a PST file. Use a recursive method to browse all the folders (including any nested folders) and call the [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(byte[]\)) method to get Outlook messages into an instance of the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class. After that, call the [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#save\(java.io.OutputStream\)) method to save the message to either disk or stream in MSG format. The following code snippet shows you how to extract messages from PST file is give below.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.fromFile(path);

        // get the Display Format of the PST file
        System.out.println("Display Format: " + pst.getFormat());

        // get the folders and messages information
        FolderInfo folderInfo = pst.getRootFolder();

        // Call the recursive method to extract msg files from each folder
        extractMsgFiles(folderInfo, pst);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void extractMsgFiles(FolderInfo folderInfo, PersonalStorage pst) {
    // display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Saving message {0} ...." + messageInfo.getSubject());
        // get the message in MapiMessage instance
        MapiMessage message = pst.extractMessage(messageInfo);
        // save this message to disk in msg format
        message.save(message.getSubject().replace(":", " ") + ".msg");
        // save this message to stream in msg format
        ByteArrayOutputStream messageStream = new ByteArrayOutputStream();
        message.save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            extractMsgFiles(subfolderInfo, pst);
        }
    }
}
~~~
### **Saving Messages Directly from PST to Stream**
To save messages from a PST file directly to stream, without extracting the MsgInfo for messages, use the [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#saveMessageToStream\(java.lang.String,%20java.io.OutputStream\)) method. The following code snippet shows you how to save messages directly from PST to stream.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

// Load the Outlook file
String path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
try (PersonalStorage personalStorage = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (ByteArrayOutputStream memeorystream = new ByteArrayOutputStream()) {
            personalStorage.saveMessageToStream(messageInfo.getEntryIdString(), memeorystream);
        }
    }
}

// Save message to file
try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (FileOutputStream fs = new FileOutputStream(new File(dataDir + messageInfo.getSubject() + ".msg"))) {
            pst.saveMessageToStream(messageInfo.getEntryIdString(), fs);
        }
    }
}

try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");

    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    for (String entryId : inbox.enumerateMessagesEntryId()) {
        try (ByteArrayOutputStream ms = new ByteArrayOutputStream()) {
            pst.saveMessageToStream(entryId, ms);
        }
    }
}
~~~
### **Extracting n Number of Messages from a PST File**
The following code snippet shows you how to extract a given number of messages from a PST. Simply provide the index for the first message, and the total number of messages to be extracted.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~
## **Delete Items from PST Files**
[Add Messages to PST Files](#adding-messages-to-pst-files) showed how to add messages to PST files. It is, of course, also possible to delete items (contents) from a PST file and it may also be desirable to delete messages in bulk. Items from a PST file can be deleted using the [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) method. The API also provides [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItems\(java.lang.Iterable\)) method to delete items in bulk from the PST file.
### **Deleting Messages from PST Files**
This articles shows how to Use the [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo) class to access specific folders in a PST file. To delete messages from the Sent subfolder of a previously loaded or created PST file:

1. Create an instance of the [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo) class and load it with the contents of the sent subfolder.
1. Delete messages from the Sent folder by calling the [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) method and passing the [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#getEntryId\(\)) as a parameter. The following code snippet shows you how to delete messages from a PST file's Sent subfolder.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.getPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.getContents();
for (MessageInfo msgInfo : msgInfoColl) {
    System.out.println(msgInfo.getSubject() + ": " + msgInfo.getEntryIdString());
    if (msgInfo.getSubject().equals("some delete condition")) {
        // Delete this item
        folderInfo.deleteChildItem(msgInfo.getEntryId());
        System.out.println("Deleted this message");
    }
}
~~~
### **Deleting Folders from PST Files**

You can delete a PST folder by moving it to the Deleted Items folder.


~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Empty folder");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~
The advantage of this method is that the deleted folder can be easily recovered.


~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Some folder");
pst.moveItem(someFolder, pst.getRootFolder());
~~~
You can also permanently remove a folder from the Deleted Items folder, if necessary.


~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~
The [deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) method can be used for any folders if you want to immediately and permanently delete subfolder, bypassing the Deleted Items folder.


~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~
### **Delete Items in Bulk from PST File**
Aspose.Email API can be used to delete items in bulk from a PST file. This is achieved using the [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItems\(java.lang.Iterable\)) method which accepts a list of Entry ID items referring to the items to be deleted. The following code snippet shows you how to delete Items in bulk from PST file.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.getFrom().contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());
    List<String> deleteList = new ArrayList<String>();
    for (MessageInfo messageInfo : messages) {
        deleteList.add(messageInfo.getEntryIdString());
    }

    // delete messages having From = "someuser@domain.com"
    inbox.deleteChildItems(deleteList);
}
~~~
## **Search Messages and Folders in a PST by Criterion**
Personal Storage (PST) files can contain a huge amount of data and searching for data that meets a specific criteria in such large files needs to include multiple check points in the code to filter the information. With the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/PersonalStoragequerybuilder) class, Aspose.Email makes it possible to search for specific records in a PST based on a specified search criteria. A PST can be searched for messages based on search parameters such as sender, receiver, subject, message importance, presence of attachments, message size, and even message ID. The [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/PersonalStoragequerybuilder) can also be used to search for subfolders.
### **Searching Messages and Folders in PST**
The following code snippet shows you how to use the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/PersonalStoragequerybuilder) class to search for contents in a PST based on different search criteria. For example, it shows searching a PST based on:

- Message importance.
- Message class.
- Presence of attachments.
- Message size.
- Message date.
- Unread messages.
- Unread messages with attachments, and
- folders with specific subfolder name.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalStorage.getRootFolder().getSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.getImportance().equals((int) MapiImportance.High);
    MessageInfoCollection messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with High Imp:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    builder.getMessageClass().equals("IPM.Note");
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with IPM.Note:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.getImportance().equals((int) MapiImportance.High);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with atts: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.getMessageSize().greater(15000);
    messages = folder.getContents(builder.getQuery());
    System.out.println("messags size > 15Kb:" + messages.size());

    java.util.Calendar c = java.util.Calendar.getInstance();

    builder = new PersonalStorageQueryBuilder();
    // Messages by Current Date
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    builder.getSentDate().on(c.getTime(), DateComparisonType.ByDate);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages by Current Date: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages between Dates
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    c.set(2020,  0, 1, 0, 0, 0);
    builder.getSentDate().since(c.getTime());
    c.set(2021,  0, 1, 0, 0, 0);
    builder.getSentDate().before(c.getTime());
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages between Dates: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread msgs with atts: " + messages.size());

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.getFolderName().equals("SubInbox");
    FolderInfoCollection folders = folder.getSubFolders(builder.getQuery());
    System.out.println("Folder having subfolder: " + folders.size());

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.hasSubfolders();
    folders = folder.getSubFolders(builder.getQuery());
    System.out.println(folders.size());
}
~~~
### **Searching for a String in PST with the Ignore Case Parameter**
The following code snippet shows you how to search for a string in PST with the ignore case parameter.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CaseSensitivity.pst", FileFormatVersion.Unicode)) {
    FolderInfo folderinfo = personalStorage.createPredefinedFolder("Inbox", StandardIpmFolder.Inbox);
    folderinfo.addMessage(MapiMessage.fromMailMessage(MailMessage.load("Sample.eml")));
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // IgnoreCase is True
    builder.getFrom().contains("automated", true);
    MailQuery query = builder.getQuery();
    MessageInfoCollection coll = folderinfo.getContents(query);
    System.out.println(coll.size());
}
~~~

### **Searching for Message Subjects by Multiple Keywords in a PST File**
You can use [MailQueryBuilder.or](https://reference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) method to find messages with a subject containing at least one of the specified words as shown below:

~~~java
PersonalStorageQueryBuilder builder1 = new PersonalStorageQueryBuilder();
builder1.getSubject().contains("Review"); // 'Review' is key word for the search

PersonalStorageQueryBuilder builder2 = new PersonalStorageQueryBuilder();
builder2.getSubject().contains("Error"); // 'Error' is also key word for the search

PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.or(builder1.getQuery(), builder2.getQuery()); // message subjects must contain 'Review' or 'Error' words

try (PersonalStorage storage = PersonalStorage.fromFile("example.pst"))
{
    FolderInfo folderInfo = storage.getRootFolder().getSubFolder("Inbox");
    MessageInfoCollection messageInfos = folderInfo.getContents(queryBuilder.getQuery());

    for (MessageInfo messageInfo : messageInfos)
    {
        System.out.println(messageInfo.getSubject());
    }
}
~~~

## **Move Items to Other Folders of PST File**
Aspose.Email makes it possible to move items from a source folder to another folder in the same Personal Storage (PST) file. This includes:

- Moving a specified folder to a new parent folder.
- Moving a specified messages to a new folder.
- Moving the contents to a new folder.
- Moving subfolders to a new parent folder.

The following code snippet shows you how to move items such as messages and folders from a source folder to another folder in the same PST file.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
try (PersonalStorage personalStorage = PersonalStorage.fromFile("test.pst")) {
    FolderInfo inbox = personalStorage.getPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.getSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.moveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.getContents();
    personalStorage.moveItem(contents.get(0), deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.moveSubfolders(deleted);
    subfolder.moveContents(deleted);
}
~~~
## **Updating Message Properties in a PST File**
It's sometimes required to update certain properties of messages such as changing the subject, marking message importance and similarly others. Updating a message in a PST file, with such changes in the message properties, can be achieved using the [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#changeMessages\(java.lang.Iterable,%20com.aspose.email.MapiPropertyCollection\)) method. This article shows how to update messages in bulk in a PST file for changes in the properties. The following code snippet shows you how to update properties of messages in bulk mode for multiple messages in a PST file.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get Requierd Subfolder
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.getFrom().contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());

// Save (MessageInfo,EntryIdString) in List
List<String> changeList = new ArrayList<String>();
for (MessageInfo messageInfo : messages) {
    changeList.add(messageInfo.getEntryIdString());
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, "New Subject".getBytes(Charset.forName("utf-16le"))));
updatedProperties.add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.getBytesInt64(2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.changeMessages(changeList, updatedProperties);
~~~
## **Updating Custom Properites in a PST File**
Sometimes its required to mark items that are processed with in the PST file. Aspose.Email API allows to achieve this using the MapiProperty and MapiNamedProperty. The following methods are helpful in achieving this.

- ctor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)
- FolderInfo.changeMessages(MapiPropertyCollection updatedProperties) - changes all messages in folder
- PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties) - change message properties


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/" + "Sub.pst";

    try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
        FolderInfo testFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

        // Create the collection of message properties for adding or updating
        MapiPropertyCollection newProperties = new MapiPropertyCollection();

        // Normal, Custom and PidLidLogFlags named property
        MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W, "test_address@org.com".getBytes(Charset.forName("utf-16le")));
        MapiProperty namedProperty1 = new MapiNamedProperty(generateNamedPropertyTag(0L, MapiPropertyType.PT_LONG), "ITEM_ID", UUID.randomUUID(),
                BitConverter.getBytesInt64(123));
        MapiProperty namedProperty2 = new MapiNamedProperty(generateNamedPropertyTag(1L, MapiPropertyType.PT_LONG), 0x0000870C,
                UUID.fromString("0006200A-0000-0000-C000-000000000046"), BitConverter.getBytesInt64(0));
        newProperties.add(namedProperty1.getTag(), namedProperty1);
        newProperties.add(namedProperty2.getTag(), namedProperty2);
        newProperties.add(property.getTag(), property);
        testFolder.changeMessages(testFolder.enumerateMessagesEntryId(), newProperties);
    }
}

private static long generateNamedPropertyTag(long index, int dataType) {
    return (((0x8000 | index) << 16) | (long) dataType) & 0x00000000FFFFFFFFL;
}
~~~
## **Extract Attachments without Extracting Complete Message**
Aspose.Email API can be used to extract attachments from PST messages without extracting the complete message first. The ExtractAttachments method of IEWSClient can be used to do this. The following code snippet shows you how to extract attachments without extracting complete message.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalstorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalstorage.getRootFolder().getSubFolder("Inbox");

    for (String messageInfo : folder.enumerateMessagesEntryId()) {
        MapiAttachmentCollection attachments = personalstorage.extractAttachments(messageInfo);

        if (attachments.size() != 0) {
            for (MapiAttachment attachment : attachments) {
                if (attachment.getLongFileName() != null && !attachment.getLongFileName().isEmpty()) {
                    if (attachment.getLongFileName().contains(".msg")) {
                        continue;
                    } else {
                        attachment.save(dataDir + "Attachments/" + attachment.getLongFileName());
                    }
                }
            }
        }
    }
}
~~~
## **Adding Files to PST**
Microsoft Outlook's key functionality is managing emails, calendars, tasks, contacts and journal entries. In addition, files can also be added to a PST folder and the resulting PST keeps record of the documents added. Aspose.Email provides the facility to add files to a folder in the same way in addition to adding messages, contacts, tasks and journal entries to PST. The following code snippet shows you how to add documents to a PST folder using Aspose.Email.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode)) {
    FolderInfo folder = personalStorage.getRootFolder().addSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.addFile(dataDir + "attachment_1.doc", null);
}
~~~
