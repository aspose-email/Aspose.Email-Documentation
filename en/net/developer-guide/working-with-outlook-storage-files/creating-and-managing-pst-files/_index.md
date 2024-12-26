---
title: Creating and Managing PST Files
ArticleTitle: Creating and Managing PST Files
type: docs
weight: 10
url: /net/create-and-manage-pst-files/
---

As well as parsing an existing PST file, Aspose.Email provides the means to create a PST file from scratch. This article demonstrates how to create Outlook PST files and add sub-folders or messages to them.

## **Creating PST Files**

To create a new PST file on a local disk, you will need to use the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class. With this class, you can create, read, and manipulate PST files in your .NET applications. Create a storage file from scratch with a line of code:

```csharp
// Create new PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);
```

## **Add Sub-folders to PST**

Add a sub-folder at the root of the PST file by accessing the Root folder and then calling the [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/) method.

The following code snippet shows you how to add a subfolder called Inbox:

```csharp
// Add new folder "Test"
pst.RootFolder.AddSubFolder("Inbox");
```

## **Check the Folder Container Class**

When creating new folders or adding items to existing folders, it is important to ensure that the container class of the new item or folder aligns with the container class of the parent folder to maintain the organizational hierarchy within the PST storage file. For this purpose, Aspose.Email has the [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) property of the [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) class. The property specifies whether to enforce checking the container class of the folder being added against the container class of the parent folder. If set to 'true', an exception will be thrown if the container classes do not match. Default is 'false'.

The following code sample demonstrates the use of the [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) property to control whether an exception should be thrown when adding folders with mismatching container classes: 

```cs
using (var pst = PersonalStorage.Create("storage.pst", FileFormatVersion.Unicode))
{
    // Create a standard Contacts folder with the IPF.Contacts container class.
    var contacts = pst.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    
    // An exception will not arise. EnforceContainerClassMatching is false by default.
    contacts.AddSubFolder("Subfolder1", "IPF.Note");
    
    // An exception will occur as the container class of the subfolder being added (IPF.Note) 
    // does not match the container class of the parent folder (IPF.Contact).
    contacts.AddSubFolder("Subfolder3", new FolderCreationOptions {EnforceContainerClassMatching = true, ContainerClass = "IPF.Note"});
}
```

>Note: Ensure proper handling of exceptions when enforcing container class matching to prevent unexpected behavior during folder creation in PST.

## **Change the Folder Container Class**

Sometimes it is necessary to change the folder container class. A common example is where messages of different types (appointments, messages, etc.) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code snippet shows you how to change the container class of a folder in PST for this purpose.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst);
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Adding Files to PST**

The key functionality of Microsoft Outlook is managing emails, calendars, tasks, contacts and journal entries. In addition, files can also be added to a PST folder and the resulting PST keeps a record of the documents added. Aspose.Email provides the facility to add files to a folder in the same way together with adding messages, contacts, tasks and journal entries to PST. The following code snippet shows you how to add documents to a PST folder using Aspose.Email.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (var personalStorage = PersonalStorage.Create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode))
{
    var folder = personalStorage.RootFolder.AddSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.AddFile(dataDir + "attachment_1.doc", null);
}
```

## **Adding Messages to PST Files**

With Aspose.Email you can add messages to subfolders of a PST file that you have created or loaded. This article adds two messages from disk to the Inbox subfolder of a PST. Use the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) classes to add messages to PST files. To add messages to a PST file Inbox folder:

1. Create an instance of the FolderInfo class and load it with the contents of the Inbox folder.
2. Add messages from a disk to the Inbox folder by calling the [FolderInfo.AddMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/#addmessage) method. The [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/) class exposes the [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/#addmessages) method that enables to add large number of messages to the folder, reducing I/O operations to a disc and improving performance.

The code snippet below shows how to add messages to a PST subfolder called Inbox.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create new PST            
var personalStorage = PersonalStorage.Create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.RootFolder.AddSubFolder("Inbox");

// Select the "Inbox" folder
var inboxFolder = personalStorage.RootFolder.GetSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.AddMessage(MapiMessage.FromFile(RunExamples.GetDataDir_Outlook() + "MapiMsgWithPoll.msg"));
```

### **Add Bulk Messages with Improved Performance**

Adding individual messages to a PST implies more I/O operations to the disc and may slow down the performance. To improve the performance, messages can be added to the PST in the bulk mode to minimize I/O operations.
The [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) method allows you to add messages in bulk and can be used as in the following scenarios. In addition, the [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) event occurs when a message is added to the folder.

#### **Add Messages from Another PST**

To add messages from another PST, use the [FolderInfo.EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) method that returns `IEnumerable<MapiMessage>`:

```csharp
using var srcPst = PersonalStorage.FromFile(@"source.pst", false);
using var destPst = PersonalStorage.FromFile(@"destination.pst");

// Get the folder by name
var srcFolder = srcPst.RootFolder.GetSubFolder("SomeFolder");
var destFolder = destPst.RootFolder.GetSubFolder("SomeFolder");

destFolder.MessageAdded += new MessageAddedEventHandler(OnMessageAdded);
destFolder.AddMessages(srcFolder.EnumerateMapiMessages());


// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

#### **Add Messages from Directory**

To add messages from directory, create the `GetMessages(string pathToDir)` named iterator method that returns `IEnumerable<MapiMessage>`:

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");
var folder = pst.RootFolder.GetSubFolder("SomeFolder");
folder.MessageAdded += OnMessageAdded;
folder.AddMessages(GetMessages(@"MessageDirectory"));

// Named iterator method to read messages from directory.
static IEnumerable<MapiMessage> GetMessages(string pathToDir)
{
    string[] files = Directory.GetFiles(pathToDir, "*.msg");

    foreach (var file in files)
    {
        yield return MapiMessage.Load(file);
    }
}

// Handles the MessageAdded event.
static void OnMessageAdded(object sender, MessageAddedEventArgs e)
{
    Console.WriteLine($"Added: {e.EntryId}");
}
```

### **Load Messages from Disk**

The following code snippet shows you how to load messages from a disc.

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

The following code snippet shows you how IEnumerable Implementation can be used.

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
