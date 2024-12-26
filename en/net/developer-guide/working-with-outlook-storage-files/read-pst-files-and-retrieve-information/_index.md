---
title: Read PST Files and Retrieve Information
ArticleTitle: Read PST Files and Retrieve Information
type: docs
weight: 80
url: /net/read-pst-files-and-retrieve-information/
---

## **Read PST Files and Retrieve Information**

Aspose.Email for .NET provides an API for reading Microsoft Outlook PST files. You can load a PST file from disk or stream into an instance of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class and get the information about its contents, for example, folders, subfolders, and messages. The API also provides the capability to include search folders while traversing for messages from the PST folders.

### **Load PST File**

An Outlook PST file can be loaded in an instance of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class. The following code snippet shows you how to load the PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

### **Display Folders Information**

After loading the PST file in the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class, you can get the information about the file display name, root folder, subfolders and messages count. The following code snippet shows you how to display the name of PST file, folders and the number of messages in the folders.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

### **Get User-Defined Folders Only**

PST/OST files may contain folders which were created by a user. Aspose.Email provides the ability to access only user-defined folders by using the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) property. You can set the [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) property to **true** to get only user-defined folders. The following code snippet demonstrates the use of [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) to get user-defined folders.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

### **Check if Folder is Predefined**

When opening and inspecting the folders within a PST (Personal Storage Table) file, you can check whether each folder is a predefined folder type or a subfolder of a predefined folder type, and obtain the information about each folder.

The [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)(bool getForTopLevelParent) method allows to check whether a folder is from [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). If *getForTopLevelParent* param is true, method returns a [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) enum value for the top-level parent folder. This determines whether the current folder is a subfolder of a predefined folder. If *getForTopLevelParent* param is false, it returns a [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) enum value for the current folder.

The following code sample shows how to implement this feature into your project:

```cs
PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders();

            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");
                Console.WriteLine($"Is predefined: {folder.GetPredefinedType(false) != StandardIpmFolder.Unspecified}");
                Console.WriteLine("-----------------------------------");
            }
        }
```

### **Retrieve Parent Folder Information**

The following code snippet shows you how to retrieve parent folder information from [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

### **Retrieve Subfolder by Path**

The [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) method overload will enable you to retrieve a subfolder with the specified name from the current PST folder.

The method takes the following parameters:

- **name** - specifies the name of the subfolder to retrieve.
- **ignoreCase** - determines whether the search for the subfolder name should be case-sensitive or case-insensitive. If set to *true*, the search will be case-insensitive, otherwise, it will be case-sensitive.
- **handlePathSeparator** - specifies whether the specified folder name should be treated as a path if it contains backslashes. If set to *true*, the method will interpret the folder name as a path, attempting to navigate to the subfolder using the path. If set to *false*, the method will treat the folder name as a simple name, searching for a subfolder with an exact name match.
  
The following code sample demonstrates how to implement this method in your project:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
In this sample, the method will return a ‘Jan’ named folder that is located at the Inbox\Reports\ path relative to the root folder.
```

## **RSS Feeds and Searchable Folders**

### **Standard RSS Feeds Folder in PersonalStorage**

Aspose.Email makes it possible to retrieve a reference to the predefined folder that holds RSS feeds. This could be useful if you want to programmatically access and manipulate the RSS feeds stored in an Outlook PST file.
Give the value of RssFeeds to the [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration) enum.

The following code example shows how to get an RSS Feeds folder.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

To add an RSS Feeds folder, use the following code snippet:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

### **Parsing Searchable Folders**

A PST/OST may contain searchable folders in addition to the normal type of folders. Aspose.Email provides the [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) enumerator for specifying the messages from such search folders with [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) and [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/) methods. The following code snippet shows you how to parse searchable folders.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Browse through each folder to display folder name and number of messages
            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");

                FolderInfoCollection subFolders = folder.GetSubFolders(FolderKind.Search | FolderKind.Normal);
                foreach (FolderInfo subFolder in subFolders)
                {
                    Console.WriteLine($"Sub-folder: {subFolder.DisplayName}");
                }
            }
        }
```

### **PST File Traversal API**

The traversal API allows extracting all PST items as far as possible, without throwing out exceptions, even if some data of the original file is corrupted.
The following steps show how to use this API.

Use [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) constructor and [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) method instead of FromFile method.

The constructor allows defining a callback method.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
```

Loading and traversal exceptions will be available through the callback method.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) method returns 'true' if the file has been loaded successfully and further traversal is possible. If a file is corrupted and no traversal is possible, 'false' is returned.

```csharp
if (currentPst.Load(inputStream))
```

This allows to open and traverse even corrupted PST files without throwing out exceptions. And exceptions and corrupted items will be handled by the callback method.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
{
    if (pst.Load(@"test.pst"))
    {
        GetAllMessages(pst, pst.RootFolder);
    }
}

private static void GetAllMessages(PersonalStorage pst, FolderInfo folder)
{
    foreach (var messageEntryId in folder.EnumerateMessagesEntryId())
    {
        MapiMessage message = pst.ExtractMessage(messageEntryId);
    }
    foreach (var subFolder in folder.GetSubFolders())
    {
        GetAllMessages(pst, subFolder);
    }
}
```

## **Retrieve Item Category Colors from PST Files**

Aspose.Email allows users to retrieve category information, including names and colors, from PST files. Category data can be extracted and matched with individual PST items. Use the following API members:

- [OutlookCategoryColor](https://reference.aspose.com/email/net/aspose.email.storage.pst/outlookcategorycolor/) enum - Represents the color associated with a category.
- [PstItemCategory](https://reference.aspose.com/email/net/aspose.email.storage.pst/pstitemcategory/) class - Provides properties for category name and color.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getcategories/) method - Retrieves a list of categories with their names and colors.

The following code samples demonstrate how to retrieve all available categories from a PST file and match those associated with a specific email message.

### **Retrieve available Categories from PST**

```cs
using (var pst = PersonalStorage.FromFile("mailbox.pst"))
{
   var categories = pst.GetCategories();
   
   foreach(var category in categories)
   {
       Console.WriteLine(category);
   }
}
```

### **Match a Category Name with its Color**

```cs
using (var pst = PersonalStorage.FromFile("mailbox.pst"))
{
    // Get all categories from the PST
    var availableCategories = pst.GetCategories();
    
    // Extract a message from the PST and retrieve the list of category names for the message
    var messageCategoryList = FollowUpManager.GetCategories(pst.ExtractMessage(messageInfo));
    
    // Iterate through each category in the message and match it with the PST category list
    foreach (var messageCategory in messageCategoryList)
    {
        var category = availableCategories.Find(c => c.Name.Equals(messageCategory, StringComparison.OrdinalIgnoreCase));

        if (category != null)
        {
            // Print the category name and its associated color
            Console.WriteLine(category);
        }
        else
        {
            Console.WriteLine($"Category: {messageCategory}, Color: Not found");
        }
    }
}
```
