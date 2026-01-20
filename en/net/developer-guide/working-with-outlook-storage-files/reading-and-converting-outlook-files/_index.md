---
title: Reading and Converting Outlook Files
ArticleTitle: Reading and Converting Outlook Files
type: docs
weight: 110
url: /net/reading-and-converting-outlook-files/
---

## **Working with OST Files**

Aspose.Email for .NET provides an API for reading Microsoft Outlook OST files. You can load an OST file from a disk or a stream into an instance of the [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class to access its contents, such as folders, subfolders, and messages. Microsoft Outlook creates a PST file to store emails when using POP3 or IMAP mail servers. In contrast, it creates an OST file when Microsoft Exchange is the mail server. OST files also support larger file sizes than PST files.

### **Read OST Files**

The process for reading an OST file with Aspose.Email is exactly the same as for reading a PST file. The same code can read both PST and OST files: just provide the correct file name to the [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/) method. The following code snippet shows you how to read OST files.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

### **Convert OST to PST**

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}
Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, the OST file can be created from PST file using the same line of code with the [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/) enumerator. At present, the API supports converting OST formats to PST **except 2013/2016/2019/2021 and future versions**. The following code snippet shows you how to Convert OST to PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

For performing other operations with OST files, please refer to the following pages:

- [Read PST Files and Retrieve Information](https://docs.aspose.com/email/net/read-pst-files-and-retrieve-information/)
- [Get Messages Information from an Outlook PST File](https://docs.aspose.com/email/net/managing-messages-in-pst-files/#get-messages-information-from-an-outlook-pst-file)
- [Extract Messages from Outlook PST File and Save to Disk or Stream in MSG Format](https://docs.aspose.com/email/net/managing-messages-in-pst-files/#extracting-messages-from-pst-files)
- [Access Contact Information from Outlook PST File and Save to Disk in MSG Format](https://docs.aspose.com/email/net/managing-contacts-in-pst-files/#save-contacts-in-msg-format)

### **Convert PST to OST**

Conversion from PST to OST is not supported by Aspose.Email because OST is always created by the Outlook when adding an account and synchronizing with the mail server.
The difference between PST and OST files is that PST is only available locally. OST content is also available on the e-mail server.
So there is no need to convert PST to OST for local use.
But you can import PST into an existing account using the Import/Export wizard in Outlook.

OLM is a specific file format used by Microsoft Outlook for storing local data such as emails, attachments, notes, calendar data, contacts, tasks, history, and more. OLM files are only compatible with Outlook for Mac and cannot be opened or accessed by Outlook for Windows, which uses the PST file format instead.

## **Working with OLM Files**

### **Open OLM Files**

OLM format files can be opened in two ways:

- using constructor
- using static FromFile method

There are differences in behavior between these methods. See section below.

**Using Constructor**

To open a file, call constructor of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class and pass full file name or stream as an argument to it:

```cs
var fileName = "MyStorage.olm";
var olm = new OlmStorage(fileName);
```

**Using Static Method FromFile**

To open a file, use static method [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) and pass full file name or stream as an argument to it:

```cs
var fileName = "MyStorage.olm";
var olm = OlmStorage.FromFile(fileName);
```

### **Retrieve Folders**

To access the directory structure of an OLM file, create an instance of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class using its constructor and pass in the path to the file.
Once the file is open, access its directory structure using the [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) property. This property returns a list of [OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) objects, each representing a directory in the OLM file. 
To further explore the directory structure, access the [SubFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/subfolders/) property of each object, which returns a list of its subdirectories. By using these properties, you can navigate through the entire directory hierarchy of the OLM file and access all the directories and subdirectories it contains.

The example below displays the list of all folders in hierarchical order:

```cs
using (var olm = new OlmStorage(fileName))
{
    PrintAllFolders(olm.FolderHierarchy, string.Empty);
}

private void PrintAllFolders(List<OlmFolder> folderHierarchy, string indent)
{
    foreach (var folder in folderHierarchy)
    {
        Console.WriteLine($"{indent}{folder.Name}");
        PrintAllFolders(folder.SubFolders, indent+"-");
    }
}
```

When using the [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/fromfile/) method to open an OLM file, the [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) property will not be initialized by default and will return null. In this case, call the GetFolders method explicitly to initialize the [FolderHierarchy](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/folderhierarchy/) property and retrieve the list of directories in the OLM file:

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folders = olm.GetFolders();
}
```

Also, it’s possible to get any folder by name:

1. Call [GetFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolder/) method.
2. Pass folder name as the first argument and value, which shows whether to ignore case sensitivity when searching for a folder, as the second parameter.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    // get inbox folder by name
    OlmFolder folder = olm.GetFolder("Inbox", true);
}
```

### **List Emails**

[OlmFolder](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/) class, which represents a folder, has the following methods to get the list of emails:

- [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/) implements iteration of emails in a folder. In this case, every iteration returns [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) object, which provides short info about email.
- [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemapimessages/), also implements iteration of emails in a folder, but in this case, every iteration returns [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object, which represents the email itself, with all properties.

**Using EnumerateMessages Method**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);
    foreach (var messageInfo in folder.EnumerateMessages())
    {
        Console.WriteLine(messageInfo.Subject);
    }
}
```

**Using EnumerateMapiMessages Method**

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var msg in folder.EnumerateMapiMessages())
    {
        // save message in MSG format
        msg.Save($"{msg.Subject}.msg");
    }
}
```

### **Other useful properties**

The other useful properties of the OlmFolder class are: [HasMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/hasmessages/) and [MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) properties, which return the presence of messages in the folder and their count.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    if (folder.HasMessages)
    {
        Console.WriteLine($"Message count: {folder.MessageCount}");
    }
}
```

### **Get or Set the Modified Date of a Message**

The modified date represents the date and time when the OLM message was last modified. You can use the [OlmMessageInfo.ModifiedDate](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/modifieddate/) property to retrieve or update the modified date value of an OLM message.

Here's an example that demonstrates the usage of the property:

```cs
foreach (OlmMessageInfo messageInfo in inboxFolder.EnumerateMessages())
{
   DateTime modifiedDate = messageInfo.ModifiedDate;
}
```

### **Extract Emails and Items**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class has [ExtractMapiMessage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/) method which allows to extract emails. This method receives an [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) object.

```cs
using (var olm = OlmStorage.FromFile(fileName))
{
    var folder = olm.GetFolder("Inbox", true);

    foreach (var messageInfo in folder.EnumerateMessages())
    {
        if (messageInfo.Date == DateTime.Today)
        {
            // Extracts today's messages form Inbox
            var msg = olm.ExtractMapiMessage(messageInfo);
        }
    }
}
```

#### **Using Traversal API**

You can extract all items from an Outlook OLM file as far as possible, without throwing out exceptions, even if some data of the original file is corrupted. To perform this, use [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#constructors) constructor and [Load(string fileName)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method instead of FromFile method. The constructor allows defining a callback method.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
```

The callback method makes loading and traversal exceptions available.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```cs
if (olm.Load(fileName))
```

The following code snippet and the steps show how to use this API:

1. Create a new instance of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class, passing an exception handling callback to handle any exceptions encountered during the process.
2. Load the OLM file by calling the [Load](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/load/#load_1) method of the OlmStorage instance.
3. If the OLM file is successfully loaded, obtain the folder hierarchy by calling the [GetFolders](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getfolders/) method on the OlmStorage instance. This returns a list of OlmFolder objects.
4. Call the ExtractItems method, passing the OlmStorage instance and the list of OlmFolder objects.
5. In the ExtractItems method, iterate through each folder in the folders list.
6. If the folder contains messages (emails), print the folder name to the console using Console.WriteLine(folder).
7. Iterate through the messages in the current folder by calling the EnumerateMessages method on the OlmStorage instance, passing the current folder as an argument.
8. Print the subject of each message to the console using Console.WriteLine(msg.Subject).
9. If the folder has subfolders, recursively call the ExtractItems method again, passing the OlmStorage instance and the subfolders of the current folder.

```cs
using (var olm = new OlmStorage((exception, id) => { /* Exception handling  code. */ }))
{
    if (olm.Load(fileName))
    {
        var folderHierarchy = olm.GetFolders();
        ExtractItems(olm, folderHierarchy);
    }
}

private static void ExtractItems(OlmStorage olm, List<OlmFolder> folders)
{
    foreach (var folder in folders)
    {
        if (folder.HasMessages)
        {
            Console.WriteLine(folder);

            foreach (var msg in olm.EnumerateMessages(folder))
            {
                Console.WriteLine(msg.Subject);
            }
        }

        if (folder.SubFolders.Count > 0)
        {
            ExtractItems(olm, folder.SubFolders);
        }
    }
}
```

#### **Extract Messages by Identifiers**
  
Sometimes it is required to extract selected messages by identifiers. For example, your application stores identifiers in a database and extracts a message on demand. This is the efficient way to avoid traversing through the entire storage each time to find a specific message to extract. This feature is available for OLM storages. The [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) property of the [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/#olmmessageinfo-class) class gets the message entry identifier. The overloaded [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) method of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class gets the message from OLM.

The code below shows how to extract messages from OLM by identifiers.

The code performs the following steps:

1. Initiates a foreach loop to iterate through a list of [OlmMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/) objects. The loop uses the [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/enumeratemessages/#enumeratemessages) method of the olmFolder object to retrieve a list of all messages in the current folder being iterated.
2. The loop extracts the corresponding MapiMessage object from the storage by calling the [ExtractMapiMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/extractmapimessage/#extractmapimessage_1) method of [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class, passing in the [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmmessageinfo/entryid/) of the current message as a parameter.

The retrieved MapiMessage object can be used to access and manipulate the contents of the message. The loop continues until all messages in the folder have been processed.

```cs
  foreach (OlmMessageInfo msgInfo in olmFolder.EnumerateMessages())
  {
      MapiMessage msg = storage.ExtractMapiMessage(msgInfo.EntryId);
  }
```

### **Folder Path Retrieval**

You may also get the folder path of folders in the OML file. Aspose.Email provides [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) property which returns the folder path. The following code snippet demonstrates the use of [OlmFolder.Path](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/path/) property to get the folder paths in the OML file.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintPath(storage, storage.FolderHierarchy);

public static void PrintPath(OlmStorage storage, List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        // print the current folder path
        Console.WriteLine(folder.Path);

        if (folder.SubFolders.Count > 0)
        {
            PrintPath(storage, folder.SubFolders);
        }
    }
}
```

### **Count Items in Folder**

You may also count the number of items in the folder. Aspose.Email provides [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) property which returns the number of items in the folder. The following code snippet demonstrates the use of [OlmFolder.MessageCount](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmfolder/messagecount/) property to get the number of items in the folders of the OML file.

```cs
var storage = new OlmStorage("SampleOLM.olm");
PrintMessageCount(storage.FolderHierarchy);

public static void PrintMessageCount(List<OlmFolder> folders)
{
    foreach (OlmFolder folder in folders)
    {
        Console.WriteLine("Message Count [" + folder.Name + "]: " + folder.MessageCount);
    }
}
```

### **Get Total Items Count of OlmStorage**

[OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class also has [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) method which returns the total number of message items contained in the OLM storage.
  
```cs
  using (var olm = new OlmStorage("storage.olm"))
  {
     var count = olm.GetTotalItemsCount();
  }
```

### **Outlook Category Colours Retrieval**

To work with category colors or Outlook item categories stored in OLM files, Aspose.Email offers the following solutions:

- [OlmItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmitemcategory/#olmitemcategory-class) class - represents Outlook item categories which are available by their name and associated colors, represented in hexadecimal format.
- [GetCategories()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/getcategories/) method of the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class - retrieves category list.

The following code sample demonstrates how to get all used categories from OML storage:

```cs
using (var olm = OlmStorage.FromFile("storage.olm"))
{
    var categories = olm.GetCategories();
    
    foreach (var category in categories)
    {
        Console.WriteLine($"Category name: {category.Name}");
        
        //Color is represented as a hexadecimal value: #rrggbb
        Console.WriteLine($"Category color: {category.Color}");
    }
}
```

The code sample below shows how to get a message category color:

```cs
foreach (var msg in olm.EnumerateMessages(folder))
{
    if (msg.Categories != null)
    {
        foreach (var msgCategory in msg.Categories)
        {
            Console.WriteLine($"Category name: {msgCategory}");
            var categoryColor = cat.First(c => c.Name.Equals(msgCategory, StringComparison.OrdinalIgnoreCase)).Color;
            Console.WriteLine($"Category color: {categoryColor}");
        }
    }
}
```

### **Convert OLM to PST**

[OLM](https://docs.fileformat.com/email/olm/) is a database file format used by Microsoft Outlook for Mac systems. OLM files store email messages, calendar data, contact data, and application settings. An OLM file isn’t supported by Outlook for Windows. Thus, it is not possible to open an Outlook for Mac (OLM) file in Outlook for Windows. If you want to migrate your mailbox from Outlook for Mac to Outlook for Windows, it's necessary to convert the Outlook for Mac OLM file to Outlook PST file format.

**Code Steps**

To convert an OLM file to PST follow the steps given below:

1. Create an instance of [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class to open source OLM.
2. Open a source OLM file.
3. Create a new PST file using [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Create a GetContainerClass method to map the message class to a folder class.
5. Create an AddToPst method that recursively reads each folder and its messages from OLM using EnumerateMapiMessages method and adds them to the PST in the same order using AddSubFolder and AddMessage methods.

**Code sample**

The following code sample shows how to convert OLM to PST.

**Main** method:

```cs
// create an instance of OlmStorage class to open source OLM
using (var olm = new OlmStorage("my.olm"))
// create a new PST file
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    // recursively reads each folder and its messages 
    // and adds them to the PST in the same order
    foreach (var olmFolder in olm.FolderHierarchy)
    {
        AddToPst(pst.RootFolder, olmFolder);
    }
} 
```

**GetContainerClass** method implementation:

```cs
public string GetContainerClass(string messageClass)
{
    if (messageClass.StartsWith("IPM.Contact") || messageClass.StartsWith("IPM.DistList"))
    {
        return "IPF.Contact";
    }

    if (messageClass.StartsWith("IPM.StickyNote"))
    {
        return "IPF.StickyNote";
    }

    if (messageClass.StartsWith("IPM.Activity"))
    {
        return "IPF.Journal";
    }

    if (messageClass.StartsWith("IPM.Task"))
    {
        return "IPF.Task";
    }

    if (messageClass.StartsWith("IPM.Appointment") || messageClass.StartsWith("IPM.Schedule.meeting"))
    {
        return "IPF.Appointment";
    }

    return "IPF.Note";
}
```

**AddToPst** method implementation:

```cs
public void AddToPst(FolderInfo pstFolder, OlmFolder olmFolder)
{
    FolderInfo pstSubFolder = pstFolder.GetSubFolder(olmFolder.Name);

    foreach (var msg in olmFolder.EnumerateMapiMessages())
    {
        if (pstSubFolder == null)
        {
            pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name, GetContainerClass(msg.MessageClass));
        }

        pstSubFolder.AddMessage(msg);
    }

    if (pstSubFolder == null)
    {

        pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name);
    }

    foreach (var olmSubFolder in olmFolder.SubFolders)
    {
        AddToPst(pstSubFolder, olmSubFolder);
    }
}
```