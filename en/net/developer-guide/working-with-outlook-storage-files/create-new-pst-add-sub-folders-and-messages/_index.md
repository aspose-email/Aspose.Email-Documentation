---
title: Create New PST, Add Sub-folders and Messages
type: docs
weight: 10
url: /net/create-new-pst-add-sub-folders-and-messages/
---


As well as parsing an existing PST file, Aspose.Email provides the means to create a PST file from scratch. This article demonstrates how to create an Outlook PST file and add a subfolder to it.

1. [Creating a new PST file](#creating-a-new-pst-file).
1. [Changing Container class of a folder](#changing-a-folders-container-class).
1. [Add Bulk Messages with Improved Performance](#add-bulk-messages-with-improved-performance) 

## **Create a new PST file**

Use the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class to create a PST file at some location on a local disk. To create a PST file from scratch:

1. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
1. Add a sub-folder at the root of the PST file by accessing the Root folder and then calling the [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder/) method. 

The following code snippet shows you how to create a PST file and add a subfolder called Inbox.

```csharp
// Create new PST
using var pst = PersonalStorage.Create(path, FileFormatVersion.Unicode);

// Add new folder "Test"
pst.RootFolder.AddSubFolder("Inbox");
```
## **Container Class Matching Check when Adding a Folder to PST**

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

## **Changing the Folder Container Class**

Sometimes it is necessary to change the folder container class. A common example is where messages of different types (appointments, messages, etc.) are added to the same folder. In such cases, the folder class needs to be changed for all elements in the folder to display properly. The following code snippet shows you how to change the container class of a folder in PST for this purpose.

```csharp
using var pst = PersonalStorage.FromFile("PersonalStorage1.pst);
var folder = pst.RootFolder.GetSubFolder("Inbox");

folder.ChangeContainerClass("IPF.Note");
```

## **Add Bulk Messages with Improved Performance**

Adding individual messages to a PST implies more I/O operations to the disc and may slow down the performance. To improve the performance, messages can be added to the PST in the bulk mode to minimize I/O operations.
The [AddMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessages/) method allows you to add messages in bulk and can be used as in the following scenarios. In addition, the [MessageAdded](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/messageadded/) event occurs when a message is added to the folder.

### **Add Messages from Another PST**

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

### **Add Messages from Directory**

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

