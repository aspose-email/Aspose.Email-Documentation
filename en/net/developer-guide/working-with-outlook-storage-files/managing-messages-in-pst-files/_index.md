---
title: Managing Messages in PST Files
ArticleTitle: Managing Messages in PST Files
type: docs
weight: 20
url: /net/managing-messages-in-pst-files/
---

## **Get Messages Information from an Outlook PST File**

In [Read PST Files and Retrieve Information](https://docs.aspose.com/email/net/read-pst-files-and-retrieve-information/) article we discussed how to load an Outlook PST file and browse its folders to get the folder names and the number of messages in them. This article explains how to read all the folders and subfolders in the PST file and display the information about messages, for example, subject, sender, and recipients. The Outlook PST file may contain nested folders. To get message information from these, as well as the top-level folders, use a recursive method to read all the folders. The following code snippet shows you how to reads an Outlook PST file and display the folder and message contents recursively.

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

This article shows how to read Microsoft Outlook PST files and extract messages. The messages are then saved to a disk in MSG format.

{{% alert %}}
**Try it out!**

Run the [ConversationThread](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ConversationThread) simple app project, and explore an interesting usage of Aspose.Email's features to read emails from PST and find conversation threads.
{{% /alert %}}

The following code snippet shows you how to extract messages from a PST file:

- Use a recursive method to browse all the folders (including any nested folders) and call the PersonalStorage.ExtractMessage() method to get Outlook messages into an instance of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class.
- After that, call the MapiMessage.Save() method to save the message to either a disk or a stream in MSG format.

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

## **Identifying MAPI Item Types**

The [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) enum represents a MAPI item type that can be explicitly converted into an object of the corresponding class derived from the [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface) interface. This way users can avoid checking the [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) property value before message conversion.

The following code sample shows how to define a type for the item to be converted:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Non-supported type. MapiMessage cannot be converted to an appropriate item type.
        // Just use in MSG format.
        case MapiItemType.None:
            break;
        // An email message. Conversion isn't required.
        case MapiItemType.Message:
            break;
        // A contact item. Can be converted to MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // A calendar item. Can be converted to MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // A distribution list. Can be converted to MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // A Journal entry. Can be converted to MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // A StickyNote. Can be converted to MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // A Task item. Can be converted to MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```

## **Message Search and Retrieval**

Aspose.Email provides the following overloaded methods of the [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) class to filter and retrieve messages:

- IEnumerable<MessageInfo> [EnumerateMessages(MailQuery mailQuery)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/#enumeratemessages_2) - Filter messages using a MailQuery.
- IEnumerable<MessageInfo> [EnumerateMessages(MessageKind kind)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/#enumeratemessages_1) - Retrieve messages by type (MessageKind).
- IEnumerable<MessageInfo> [EnumerateMessages(int startIndex, int count)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/#enumeratemessages_3) - Paginate message retrieval using a starting index and count.

### **Paginated Retrieval of Folder Contents**

When working with large PST folders, retrieving all messages at once can be inefficient. To improve performance and control, Aspose.Email for .NET offers pagination support in the [FolderInfo.GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#methods) method. This method retrieves a subset of messages that match the specified query, starting from a given index and limited by a count. This allows you to fetch messages in smaller, manageable batches. The method takes the following parameters:

```
IList<MessageInfo> FolderInfo.GetContents(MailQuery query, int startIndex, int count)
```

- *query* — a filter to apply to messages (optional)

- *startIndex* — the zero-based index to start retrieving from

- *count* — the number of messages to return

The code sample below demonstrates how to implement this method into a project:

```cs
// Load the PST file
using (var pst = PersonalStorage.FromFile(fileName))
{
    // Access a specific subfolder
    var folder = pst.RootFolder.GetSubFolder("Inbox");

    // Build a query to filter messages by sender address
    var queryBuilder = new PersonalStorageQueryBuilder();
    queryBuilder.From.Contains("report-service", true);

    // Define the page size
    int pageSize = 5;

    // Retrieve and process messages in pages
    for (int pageIndex = 0; pageIndex < 6; pageIndex++)
    {
        int startIndex = pageIndex * pageSize;

        // Get a page of messages
        var messages = folder.GetContents(queryBuilder.GetQuery(), startIndex, pageSize);

        foreach (MessageInfo messageInfo in messages)
        {
            // Output basic info about each message
            Console.WriteLine($"Subject: {messageInfo.Subject}, Sender: {messageInfo.SenderRepresentativeName}");
        }
    }
}
```



### **Save Messages Directly from PST to Stream**

To save messages from a PST file directly to a stream, without extracting the MsgInfo for messages, use the SaveMessageToStream() method. The following code snippet shows you how to save messages directly from PST to a stream.

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

### **Extract Specific Number of Messages**

The following code snippet shows you how to extract a given number of messages from a PST. Simply provide the index for the first message, and the total number of messages to be extracted.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
FolderInfo inbox = personalStorage.RootFolder.GetSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.GetContents(10, 100);
```

### **Get Total Items Count from PST**

Aspose.Email provides the [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) method of the [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/#personalstoragestore-property) property. It returns the total number of message items contained in the PST.

The following code sample shows how to retrieve the total count of items (messages, appointments, contacts, etc.) stored within the PST file:

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var count = pst.Store.GetTotalItemsCount();
}
```

### **Extract Attachments without Extracting Complete Message**

Aspose.Email API can be used to extract attachments from PST messages without extracting the complete message first. The [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/#extractattachments) method of [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) can be used to do this. The following code snippet shows you how to extract attachments without extracting a complete message.

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

## **Extract Message Recipients from PST Files**

Recipients of a message can be extracted from PST files using a message entry ID. This feature is available in the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class. The code samples below demonstrate how to extract message recipients:

**by EntryD** (using the [ExtractRecipients(string entryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractrecipients/#extractrecipients_1) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class)

```cs
using (var pst = PersonalStorage.FromFile(fileName))
{  
    // Recipients are extracted using the entry ID
    var recipients = pst.ExtractRecipients("AAAAADzSMygQQFJOkKwVhb8v5EUkASAA");
}
```

**from MessageInfo** (using the [MapiRecipientCollection ExtractRecipients(MessageInfo messageInfo)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractrecipients/#extractrecipients) method)

```cs
using (var pst = PersonalStorage.FromFile(fileName))
{  
    // The "Inbox" folder is obtained
    var folder = pst.RootFolder.GetSubfolder("Inbox");

    // Each message in the "Inbox" folder is iterated
    foreach (var messageInfo in folder.EnumerateMessages())
    {
        // Recipients are extracted from each message
        var recipients = pst.ExtractRecipients(messageInfo);
    }
}
```

## **Searching Messages and Folders**

### **Search by Criteria**

Personal Storage (PST) files can contain a huge amount of data. Searching for data, that meets a specific criteria in such large files, needs to include multiple check points in the code to filter the information. With the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) class, Aspose.Email makes it possible to search for specific records in a PST based on a specified search criteria. A PST can be searched for messages based on search parameters such as sender, receiver, subject, message importance, presence of attachments, message size, and even message ID. The [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) can also be used to search for subfolders.

### **Searching Messages and Folders in PST**

The following code snippet shows you how to use the [PersonalStorageQueryBuilder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/) class to search for contents in a PST based on different search criteria. For example, it shows searching a PST based on:

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

### **Ignore Case Parameter Search**

The following code snippet shows you how to search for a string in PST with the ignore case parameter.

```csharp
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

### **Search Message Subjects by Multiple Keywords**

You can use [MailQueryBuilder.Or](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) method to find messages with a subject containing at least one of the specified words as shown below:

```csharp
var builder1 = new PersonalStorageQueryBuilder();
builder1.Subject.Contains("Review"); // 'Review' is key word for the search

var builder2 = new PersonalStorageQueryBuilder();
builder2.Subject.Contains("Error"); // 'Error' is also key word for the search

var queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.Or(builder1.GetQuery(), builder2.GetQuery()); // message subjects must contain 'Review' or 'Error' words

using (var storage = PersonalStorage.FromFile("example.pst"))
{
    var folderInfo = storage.RootFolder.GetSubFolder("Inbox");
    var messageInfos = folderInfo.GetContents(queryBuilder.GetQuery());

    foreach (var messageInfo in messageInfos)
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

## **Manipulating Messages**

### **Move Items to Other Folders**

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

### **Update Message Properties**

It's sometimes required to update certain properties of messages such as changing the subject, marking message importance and similarly others. Updating a message in a PST file, with such changes in the message properties, can be achieved using the [FolderInfo.ChangeMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/changemessages/#changemessages/) method. This article shows how to update messages in bulk in a PST file for changes in the properties. The following code snippet shows you how to update properties of messages in bulk mode for multiple messages in a PST file.

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

### **Update Custom Properites**

Sometimes its required to mark items that are processed with in the PST file. Aspose.Email API allows to achieve this using the MapiProperty and MapiNamedProperty. The following methods are helpful in achieving this.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, Guid propertyGuid, byte[] propertyValue)
- FolderInfo.ChangeMessages(MapiPropertyCollection updatedProperties) - changes all messages in folder
- PersonalStorage.ChangeMessage(string entryId, MapiPropertyCollection updatedProperties) - changes message properties

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

### **Delete Messages**

This articles shows how to use the [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) class to access specific folders in a PST file. To delete messages from the Sent subfolder of a previously loaded or created PST file:

1. Create an instance of the [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) class and load it with the contents of the sent subfolder.
1. Delete messages from the Sent folder by calling the [FolderInfo.DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) method and passing the [MessageInfo.EntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/entryid/) as a parameter. The following code snippet shows you how to delete messages from a PST file Sent subfolder.

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

### **Delete Folders**

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

The [DeleteChildItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditem/#deletechilditem) method can be used for any folders if you want to immediately and permanently delete a subfolder, bypassing the Deleted Items folder.

```csharp
FolderInfo someFolder = pst.RootFolder.GetSubFolder("Some folder");
pst.RootFolder.DeleteChildItem(someFolder.EntryId);
```

### **Delete Items from PST**

Delete items (folders or messages) from a Personal Storage Table (PST) using the unique entryId associated with the item by calling the DeleteItem(string entryId) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.

The following code snippet can be used to call the DeleteItem method and pass the entryId as a parameter:

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.DeleteItem(entryId);

// ...
```

**Please Note:**

- This method will permanently delete the item from the PST and cannot be undone. Exercise caution when using this method to avoid accidental data loss.
- As per standard conventions, ensure that the entryId is valid and corresponds to an existing item within the PST. 
- Otherwise, an exception will be thrown. It is advisable to have a backup of the PST or implement suitable measures to recover deleted items if needed.

### **Bulk Deletion**

Aspose.Email API can be used to delete items in bulk from a PST file. This is achieved using the [DeleteChildItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/deletechilditems/#deletechilditems) method which accepts a list of Entry ID items referring to the items to be deleted. The following code snippet shows you how to delete Items in bulk from PST file.

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

## **Recover Soft-Deleted Items from PST and OST Files**

Aspose.Email for .NET provides a method to recover soft deleted items from PST and OST files. This functionality is implemented through the `PersonalStorage` class, which includes the [FindAndExtractSoftDeletedItems](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findandextractsoftdeleteditems/) method. This method allows you to locate and restore items that have been soft deleted, enabling you to recover important data that might otherwise be lost. The recovered items are saved in their respective folders as `.msg` files, ensuring that the original folder structure is maintained. The code sample below demonstrates how to implement this feature into your project:

```csharp
using (var pst = PersonalStorage.FromFile(fileName))
{
    // Soft deleted items are found and extracted
    var entries = pst.FindAndExtractSoftDeletedItems();

    // The recovered items are iterated through
    for (var index = 0; index < entries.Count; index++)
    {
        // Folder information is obtained by ID
        var folderInfo = pst.GetFolderById(entries[index].FolderId);

        // A directory for the folder is created if it doesn't exist
        if (!Directory.Exists(folderInfo.DisplayName))
        {
            Directory.CreateDirectory(Path.Combine(path, folderInfo.DisplayName));
        }
        
        // The restored item is obtained
        var msg = entries[index].Item;
        
        // The restored item is saved as a .msg file
        msg.Save(Path.Combine(path, folderInfo.DisplayName, $"{index}.msg"));
    }
}
```
## **Enumerate Soft-Deleted Messages in PST Files**

Soft-deleted messages in a PST file are items that have been deleted twice—first moved to Deleted Items, then removed again. Such messages are not permanently erased and can still be accessed programmatically. Aspose.Email for .NET supports retrieving these soft-deleted messages for review or recovery.

To enumerate and recover items that have been soft-deleted (deleted twice) in PST files, use the [FindAndEnumerateSoftDeletedItems()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods) method. This method retrieves an enumerable list of such items, each of them includes both the message and the ID of the folder it was deleted from.

The following code sample demonstrates how to enumerate and recover emails that have been deleted twice. It returns the [RestoredItemEntry](https://reference.aspose.com/email/net/aspose.email.storage.pst/restoreditementry/#restoreditementry-class) class which represents an entry for a soft-deleted item recovered from a PST file. The class contains the following properties:

- [Item (MapiMessage)](https://reference.aspose.com/email/net/aspose.email.storage.pst/restoreditementry/item/): The recovered message object.

- [FolderId (string)](https://reference.aspose.com/email/net/aspose.email.storage.pst/restoreditementry/folderid/): The identifier of the folder from which the message was originally deleted.

```cs
// Load the PST file
using (var pst = PersonalStorage.FromFile("archive.pst"))
{
    // Enumerate soft-deleted items
    foreach (var entry in pst.FindAndEnumerateSoftDeletedItems())
    {
        var message = entry.Item;
        var folderId = entry.FolderId;

        Console.WriteLine($"Subject: {message.Subject}");
        Console.WriteLine($"Deleted from Folder ID: {folderId}");
        Console.WriteLine("-----------------------------------");
    }
}
```

## **Split PST Files**

### **Split into Multiple PSTs**

Aspose.Email API provides the capability to split a single PST file into multiple PST files of the desired file size.

The code sample below describes the process of a file split:

1. It, first, uses the [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class to specify the file name.

2. Then, it calls the [StorageProcessedEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventhandler/#storageprocessedeventhandler-delegate) delegate to handle an StorageProcessed event.

3. The StorageProcessingEventArgs provides data for the PersonalStorage.StorageProcessing event. Its [StorageProcessingEventArgs.FileName](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessedeventargs/filename/#storageprocessedeventargsfilename-property) property allows you to retrieve the name of the PST file. For [MergeWith](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/mergewith/#mergewith_1) method it will be a name of the current pst to be merged with the main one, and for [SplitInto](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) method it will be a name of the current part.

4. Finally, [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto) overload method will launch the splitting of the PST storage into smaller-sized parts. It takes the following parameters:

- **chunkSize**: The approximate size of each chunk in bytes.
- **partFileNamePrefix**: The prefix to be added to the filename of each part of the PST. If provided, the prefix will be added to the beginning of each file name. If not provided (null or empty), the PST parts will be created without a prefix.
- **path**: The folder path where the chunks will be created.

The filename of each part follows the template: {prefix}part{number}.pst, where {prefix} represents the filename prefix (if provided), and {number} represents the number of the chunk file.

```cs
var pst = PersonalStorage.FromFile("sample.pst");

// ...

pst.StorageProcessing += (sender, args) =>
{
    Console.WriteLine("Storage processing event raised for file: " + args.FileName);
};

// ...

pst.SplitInto(5000000, "prefix_", outputFolderPath);
```

### **Split PST Based on Specified Criterion**

The following code snippet shows you how to split PST based on a specified criterion.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SpecificCriterionSplitPST-SpecificCriterionSplitPST.cs" >}}

## **Merge PST Files**

### **Merge into a Single PST**

It can also merge multiple PST files into a single PST file. Both the splitting and merging of PSTs operations can be tracked by adding events to these operations.

The following code snippet shows you how to merge into a single PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MergeMultiplePSTsInToSinglePST-MergePSTFiles.cs" >}}

{{% alert %}}
**Try it out!**

Merge and combine multiple email files online into a single one with the free [**Aspose.Email Merger App**](https://products.aspose.app/email/merger).
{{% /alert %}}

### **Merge Folders from Another PST**

The following code snippet shows you how to merge folders from another PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MergeFolderFromAnotherPSTFile-MergePSTFolders.cs" >}}
