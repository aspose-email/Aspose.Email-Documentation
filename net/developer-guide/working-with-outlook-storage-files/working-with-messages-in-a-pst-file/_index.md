---
title: Working with Messages in a PST File
type: docs
weight: 30
url: /net/working-with-messages-in-a-pst-file/
---


## **Adding Messages to PST Files**
[Create a New PST File and Add Subfolders](/email/net/create-new-pst-file-and-add-subfolders/#creating-a-new-pst-file-and-add-subfolders) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add messages to subfolders of a PST file that you have created or loaded. This article adds two messages from disk to the Inbox subfolder of a PST. Use the [PersonalStorage](https://apireference.aspose.com/email/net/aspose.email.storage.pst/personalstorage) and [FolderInfo](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo) classes to add messages to PST files. To add messages to a PST file's Inbox folder:

1. Create an instance of the FolderInfo class and load it with the contents of the Inbox folder.
1. Add messages from disk to the Inbox folder by calling the [FolderInfo.AddMessage()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/addmessage) method. The [FolderInfo](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo) class exposes the [AddMessages](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/addmessages) method that enables to add large number of messages to the folder, reducing I/O operations to disc and improving performance. A complete example can be found below, in [Adding Bulk Messages](#adding-bulk-messages).

The code snippets below shows how to add messages to a PST subfolder called Inbox.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create new PST            
PersonalStorage personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Adding Bulk Messages**
Adding individual messages to a PST implies more I/O operations to disc and hence may slow down performance. For improved performance, messages can be added to the PST in bulk mode to minimize I/O operations. The AddMessages(IEnumerable<MapiMessage> messages) method allows you to define a range of message be added to the PST for improved performance and can be used as in the following scenarios. In addition, the MessageAdded event occurs when a message is added to the folder.
### **Loading Messages from Disc**
The following code snippet shows you how to loading messages from disc.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void AddMessagesInBulkMode(string fileName, string msgFolderName)
{
    using (PersonalStorage personalStorage = PersonalStorage.FromFile(fileName))
    {
        FolderInfo folder = personalStorage.RootFolder.GetSubFolder("myInbox");
        folder.MessageAdded += OnMessageAdded;
        folder.AddMessages(new MapiMessageCollection(msgFolderName));
    }
}
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

### **IEnumerable Implementation**
The following code snippet shows you how to IEnumerable Implementation.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public class MapiMessageCollection : IEnumerable<MapiMessage>
{
    private string path;

    public MapiMessageCollection(string path)
    {
        this.path = path;
    }

    public IEnumerator<MapiMessage> GetEnumerator()
    {
        return new MapiMessageEnumerator(path);
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}

public class MapiMessageEnumerator : IEnumerator<MapiMessage>
{
    private readonly string[] files;

    private int position = -1;

    public MapiMessageEnumerator(string path)
    {
        string path1 = RunExamples.GetDataDir_Outlook();
        files = Directory.GetFiles(path1);
    }

    public bool MoveNext()
    {
        position++;
        return (position < files.Length);
    }

    public void Reset()
    {
        position = -1;
    }

    object IEnumerator.Current
    {
        get
        {
            return Current;
        }
    }

    public MapiMessage Current
    {
        get
        {
            try
            {
                return MapiMessage.FromFile(files[position]);
            }
            catch (IndexOutOfRangeException)
            {
                throw new InvalidOperationException();
            }
        }
    }
    public void Dispose()
    {
    }
}
```

### **Adding Messages from Other PST**
For adding messages from the another PST, use the [FolderInfo.EnumerateMapiMessages()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/enumeratemapimessages) method that returns IEnumerable<MapiMessage>. The following code snippet shows you how to add messages from other PST.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
private static void BulkAddFromAnotherPst(string source)
{
    using (PersonalStorage pst = PersonalStorage.FromFile(source, false))
    using (PersonalStorage pstDest = PersonalStorage.FromFile(RunExamples.GetDataDir_Outlook() + "PersonalStorageFile1.pst"))
    {
        // Get the folder by name
        FolderInfo folderInfo = pst.RootFolder.GetSubFolder("Contacts");
        MessageInfoCollection ms = folderInfo.GetContents();

        // Get the folder by name
        FolderInfo f = pstDest.RootFolder.GetSubFolder("myInbox");
        f.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
        f.AddMessages(folderInfo.EnumerateMapiMessages());
        FolderInfo fi = pstDest.RootFolder.GetSubFolder("myInbox");
        MessageInfoCollection msgs = fi.GetContents();

    }

}

/// <summary>
/// Handles the MessageAdded event.
/// </summary>
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine(e.EntryId);
    Console.WriteLine(e.Message.Subject);
}
```

## **Get Messages Information from an Outlook PST File**
In [Read Outlook PST File and Get Folders and Subfolders Information](/email/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/), we discussed loading an Outlook PST file and browse its folders to get the folder names and the number of messages in them. This article explains how to read all the folders and subfolders in the PST file and display the information about messages, for example, subject, sender, and recipients. The Outlook PST file may contain nested folders. To get message information from these, as well as the top-level folders, use a recursive method to read all the folders. The following code snippet shows you how to reads an Outlook PST file and display the folder and message contents recursively.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
       
        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.FromFile(path);

        // Get the Display Format of the PST file
        Console.WriteLine("Display Format: " + personalStorage.Format);

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.RootFolder;

        // Call the recursive method to display the folder contents
        DisplayFolderContents(folderInfo, personalStorage);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);               
    }            
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void DisplayFolderContents(FolderInfo folderInfo, PersonalStorage pst)
{
    // Display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Subject: " + messageInfo.Subject);
        Console.WriteLine("Sender: " + messageInfo.SenderRepresentativeName);
        Console.WriteLine("Recipients: " + messageInfo.DisplayTo);
        Console.WriteLine("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            DisplayFolderContents(subfolderInfo, pst);
        }
    }
}
```

## **Extracting Messages Form PST Files**
This article shows how to read Microsoft Outlook PST files and [extract messages](#extracting-messages-form-pst-files). The messages are then saved to disk in MSG format. The article also shows how to [extract a specific number of messages](#extracting-n-number-of-messages-from-a-pst-file) from a PST file. Use a recursive method to browse all the folders (including any nested folders) and call the PersonalStorage.ExtractMessage() method to get Outlook messages into an instance of the [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/index) class. After that, call the MapiMessage.Save() method to save the message to either disk or stream in MSG format. The following code snippet shows you how to extract messages from PST file is give below.


```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static void Run()
{            
    // The path to the file directory.
    string dataDir = RunExamples.GetDataDir_Outlook();

    // Load the Outlook file
    string path = dataDir + "PersonalStorage.pst";

    try
    {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.FromFile(path);

        // get the Display Format of the PST file
        Console.WriteLine("Display Format: " + pst.Format);

        // get the folders and messages information
        FolderInfo folderInfo = pst.RootFolder;

        // Call the recursive method to extract msg files from each folder
        ExtractMsgFiles(folderInfo, pst);
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }            
}

/// <summary>
/// This is a recursive method to display contents of a folder
/// </summary>
/// <param name="folderInfo"></param>
/// <param name="pst"></param>
private static void ExtractMsgFiles(FolderInfo folderInfo, PersonalStorage pst)
{
    // display the folder name
    Console.WriteLine("Folder: " + folderInfo.DisplayName);
    Console.WriteLine("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.GetContents();
    foreach (MessageInfo messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Saving message {0} ....", messageInfo.Subject);
        // get the message in MapiMessage instance
        MapiMessage message = pst.ExtractMessage(messageInfo);
        // save this message to disk in msg format
        message.Save(message.Subject.Replace(":", " ") + ".msg");
        // save this message to stream in msg format
        MemoryStream messageStream = new MemoryStream();
        message.Save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.HasSubFolders == true)
    {
        foreach (FolderInfo subfolderInfo in folderInfo.GetSubFolders())
        {
            ExtractMsgFiles(subfolderInfo, pst);
        }
    }
}
```

### **Saving Messages Directly from PST to Stream**
To save messages from a PST file directly to stream, without extracting the MsgInfo for messages, use the SaveMessageToStream() method. The following code snippet shows you how to save messages directly from PST to stream.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the file directory.
string dataDir = RunExamples.GetDataDir_Outlook();

// Load the Outlook file
string path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
using (PersonalStorage personalStorage = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (MemoryStream memeorystream = new MemoryStream())
        {
            personalStorage.SaveMessageToStream(messageInfo.EntryIdString, memeorystream);
        }
    }
}

// Save message to file
using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    foreach (MessageInfo messageInfo in inbox.EnumerateMessages())
    {
        using (FileStream fs = File.OpenWrite(messageInfo.Subject + ".msg"))
        {
            pst.SaveMessageToStream(messageInfo.EntryIdString, fs);
        }
    }
}

using (PersonalStorage pst = PersonalStorage.FromFile(path))
{
    FolderInfo inbox = pst.RootFolder.GetSubFolder("Inbox");
    
    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    foreach (string entryId in inbox.EnumerateMessagesEntryId())
    {
        using (MemoryStream ms = new MemoryStream())
        {
            pst.SaveMessageToStream(entryId, ms);
        }
    }
}            
```
### **Extracting n Number of Messages from a PST File**
The following code snippet shows you how to extract a given number of messages from a PST. Simply provide the index for the first message, and the total number of messages to be extracted.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.GetContents(10, 100);
```

## **Delete Items from PST Files**
[Add Messages to PST Files](#adding-messages-to-pst-files) showed how to add messages to PST files. It is, of course, also possible to delete items (contents) from a PST file and it may also be desirable to delete messages in bulk. Items from a PST file can be deleted using the [FolderInfo.DeleteChildItem()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/deletechilditem) method. The API also provides [FolderInfo.DeleteChildItems()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/deletechilditems) method to delete items in bulk from the PST file.
### **Deleting Messages from PST Files**
This articles shows how to Use the [FolderInfo](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo) class to access specific folders in a PST file. To delete messages from the Sent subfolder of a previously loaded or created PST file:

1. Create an instance of the [FolderInfo](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo) class and load it with the contents of the sent subfolder.
1. Delete messages from the Sent folder by calling the [FolderInfo.DeleteChildItem()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/deletechilditem) method and passing the [MessageInfo.EntryId](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/properties/entryid) as a parameter. The following code snippet shows you how to delete messages from a PST file's Sent subfolder.


```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.GetPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.GetContents();
foreach (MessageInfo msgInfo in msgInfoColl)
{
    Console.WriteLine(msgInfo.Subject + ": " + msgInfo.EntryIdString);
    if (msgInfo.Subject.Equals("some delete condition") == true)
    {
        // Delete this item
        folderInfo.DeleteChildItem(msgInfo.EntryId);
        Console.WriteLine("Deleted this message");
    }
}
```

### **Deleting Folders from PST Files**

You can delete a PST folder by moving it to the Deleted Items folder.

```csharp
using (PersonalStorage pst = PersonalStorage.FromFile(@"test.pst"))
{
    FolderInfo deletedItemsFolder = pst.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.RootFolder.GetSubFolder("Empty folder");
	  FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
    pst.MoveItem(emptyFolder, deletedItemsFolder);
	  pst.MoveItem(someFolder, deletedItemsFolder);
}
```

The advantage of this method is that the deleted folder can be easily recovered.

```csharp
FolderInfo someFolder = deletedItemsFolder.GetSubFolder("Some folder");
pst.MoveItem(someFolder, pst.RootFolder);
```

You can also permanently remove a folder from the Deleted Items folder, if necessary.

```csharp
deletedItemsFolder.DeleteChildItem(emptyFolder.EntryId);
```

The [DeleteChildItem()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/deletechilditem) method can be used for any folders if you want to immediately and permanently delete subfolder, bypassing the Deleted Items folder.


```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```

### **Delete Items in Bulk from PST File**
Aspose.Email API can be used to delete items in bulk from a PST file. This is achieved using the [DeleteChildItems()](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/deletechilditems) method which accepts a list of Entry ID items referring to the items to be deleted. The following code snippet shows you how to delete Items in bulk from PST file.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + @"Sub.pst";
using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
{
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.From.Contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());
    IList<string> deleteList = new List<string>();
    foreach (MessageInfo messageInfo in messages)
    {
        deleteList.Add(messageInfo.EntryIdString);
    }

    // delete messages having From = "someuser@domain.com"
    inbox.DeleteChildItems(deleteList);
}
```

## **Search Messages and Folders in a PST by Criterion**
Personal Storage (PST) files can contain a huge amount of data and searching for data that meets a specific criteria in such large files needs to include multiple check points in the code to filter the information. With the [PersonalStorageQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder) class, Aspose.Email makes it possible to search for specific records in a PST based on a specified search criteria. A PST can be searched for messages based on search parameters such as sender, receiver, subject, message importance, presence of attachments, message size, and even message ID. The [PersonalStorageQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder) can also be used to search for subfolders.
### **Searching Messages and Folders in PST**
The following code snippet shows you how to use the [PersonalStorageQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder) class to search for contents in a PST based on different search criteria. For example, it shows searching a PST based on:

- Message importance.
- Message class.
- Presence of attachments.
- Message size.
- Unread messages.
- Unread messages with attachments, and
- folders with specific subfolder name.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalStorage.RootFolder.GetSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.Importance.Equals((int)MapiImportance.High);
    MessageInfoCollection messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with High Imp:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    builder.MessageClass.Equals("IPM.Note");
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with IPM.Note:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.Importance.Equals((int)MapiImportance.High);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Messages with atts: " + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.MessageSize.Greater(15000);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("messags size > 15Kb:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread:" + messages.Count);

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.HasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.GetContents(builder.GetQuery());
    Console.WriteLine("Unread msgs with atts: " + messages.Count);

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.FolderName.Equals("SubInbox");
    FolderInfoCollection folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine("Folder having subfolder: " + folders.Count);

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.HasSubfolders();
    folders = folder.GetSubFolders(builder.GetQuery());
    Console.WriteLine(folders.Count);
}
```
### **Searching for a String in PST with the Ignore Case Parameter**
The following code snippet shows you how to search for a string in PST with the ignore case parameter.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

File.Delete("CaseSensitivity.pst");
using (PersonalStorage personalStorage = PersonalStorage.Create("CaseSensitivity.pst", FileFormatVersion.Unicode))
{
	FolderInfo folderinfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);
	folderinfo.AddMessage(MapiMessage.FromMailMessage(MailMessage.Load("Sample.eml")));
	PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
	// IgnoreCase is True
	builder.From.Contains("automated", true);
	MailQuery query = builder.GetQuery();
	MessageInfoCollection coll = folderinfo.GetContents(query);
	Console.WriteLine(coll.Count);
}
```

## **Move Items to Other Folders of PST File**
Aspose.Email makes it possible to move items from a source folder to another folder in the same Personal Storage (PST) file. This includes:

- Moving a specified folder to a new parent folder.
- Moving a specified messages to a new folder.
- Moving the contents to a new folder.
- Moving subfolders to a new parent folder.

The following code snippet shows you how to move items such as messages and folders from a source folder to another folder in the same PST file.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using(PersonalStorage personalStorage = PersonalStorage.FromFile("test.pst"))
{
    FolderInfo inbox = personalStorage.GetPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.GetPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.GetSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.MoveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.GetContents();
    personalStorage.MoveItem(contents[0], deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.MoveSubfolders(deleted);
    subfolder.MoveContents(deleted);
}
```

## **Updating Message Properties in a PST File**
It's sometimes required to update certain properties of messages such as changing the subject, marking message importance and similarly others. Updating a message in a PST file, with such changes in the message properties, can be achieved using the [FolderInfo.ChangeMessages](https://apireference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/changemessages/index) method. This article shows how to update messages in bulk in a PST file for changes in the properties. The following code snippet shows you how to update properties of messages in bulk mode for multiple messages in a PST file.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir);
            
// Get Requierd Subfolder 
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.From.Contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.GetContents(queryBuilder.GetQuery());

// Save (MessageInfo,EntryIdString) in List
IList<string> changeList = new List<string>();
foreach (MessageInfo messageInfo in messages)
{
    changeList.Add(messageInfo.EntryIdString);
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.Add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, Encoding.Unicode.GetBytes("New Subject")));
updatedProperties.Add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.GetBytes((long)2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.ChangeMessages(changeList, updatedProperties);
```

## **Updating Custom Properites in a PST File**
Sometimes its required to mark items that are processed with in the PST file. Aspose.Email API allows to achieve this using the MapiProperty and MapiNamedProperty. The following methods are helpful in achieving this.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- FolderInfo.ChangeMessages(MapiPropertyCollection updatedProperties) - changes all messages in folder
- PersonalStorage.ChangeMessage(string entryId, MapiPropertyCollection updatedProperties) - change message properties

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

public static void Run()
{
	// Load the Outlook file
	string dataDir = RunExamples.GetDataDir_Outlook() + "Sub.pst";
	using (PersonalStorage personalStorage = PersonalStorage.FromFile(dataDir))
	{
		FolderInfo testFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

		// Create the collection of message properties for adding or updating
		MapiPropertyCollection newProperties = new MapiPropertyCollection();

		// Normal,  Custom and PidLidLogFlags named  property
		MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W,Encoding.Unicode.GetBytes("test_address@org.com"));
		MapiProperty namedProperty1 = new MapiNamedProperty(GenerateNamedPropertyTag(0, MapiPropertyType.PT_LONG),"ITEM_ID",Guid.NewGuid(),BitConverter.GetBytes(123));
		MapiProperty namedProperty2 = new MapiNamedProperty(GenerateNamedPropertyTag(1, MapiPropertyType.PT_LONG),0x0000870C,new Guid("0006200A-0000-0000-C000-000000000046"),BitConverter.GetBytes(0));
		newProperties.Add(namedProperty1.Tag, namedProperty1);
		newProperties.Add(namedProperty2.Tag, namedProperty2);
		newProperties.Add(property.Tag, property);
		testFolder.ChangeMessages(testFolder.EnumerateMessagesEntryId(), newProperties);
	}
}

private static long GenerateNamedPropertyTag(long index, MapiPropertyType dataType)
{
	return (((0x8000 | index) << 16) | (long)dataType) & 0x00000000FFFFFFFF;
}
```

## **Extract Attachments without Extracting Complete Message**
Aspose.Email API can be used to extract attachments from PST messages without extracting the complete message first. The ExtractAttachments method of IEWSClient can be used to do this. The following code snippet shows you how to extract attachments without extracting complete message.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Outlook();

using (PersonalStorage personalstorage = PersonalStorage.FromFile(dataDir + "Outlook.pst"))
{
    FolderInfo folder = personalstorage.RootFolder.GetSubFolder("Inbox");

    foreach (var messageInfo in folder.EnumerateMessagesEntryId())
    {
        MapiAttachmentCollection attachments = personalstorage.ExtractAttachments(messageInfo);

        if (attachments.Count != 0)
        {
            foreach (var attachment in attachments)
            {
                if (!string.IsNullOrEmpty(attachment.LongFileName))
                {
                    if (attachment.LongFileName.Contains(".msg"))
                    {
                        continue;
                    }
                    else
                    {
                        attachment.Save(dataDir + @"\Attachments\" + attachment.LongFileName);
                    }
                }
            }
        }
    }
}
```

## **Adding Files to PST**
Microsoft Outlook's key functionality is managing emails, calendars, tasks, contacts and journal entries. In addition, files can also be added to a PST folder and the resulting PST keeps record of the documents added. Aspose.Email provides the facility to add files to a folder in the same way in addition to adding messages, contacts, tasks and journal entries to PST. The following code snippet shows you how to add documents to a PST folder using Aspose.Email.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (PersonalStorage personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    FolderInfo folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```
