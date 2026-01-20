---
title: Manage Mail Folders in Microsoft Graph (Aspose.Email)
ArticleTitle: Manage Mail Folders with IGraphClient
type: docs
weight: 30
url: /net/manage-mail-folders-in-microsoft-graph/
---

The Aspose.Email [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) interface provides methods to create, list, update, copy, move, and delete folders using Microsoft Graph.

## **List Folders**

Use the [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listfolders/#listfolders) method to retrieve all folders available for the current user. Each folder is returned as a [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) object, which includes properties like DisplayName, ItemId, HasSubFolders, and more.


```csharp
var folders = client.ListFolders();

foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}
```

## **List Folders Asynchronously**

The following example shows how to retrieve all folders in a mailbox and display their names using the `ListFoldersAsync` method.

```cs
var folders = await client.ListFoldersAsync();
foreach (var folder in folders)
{
    Console.WriteLine(folder.DisplayName);
}

var folderId = folders.Find(x => x.DisplayName == "Inbox").ItemId;
var msgsPage = await client.ListMessagesAsync(folderId, new PageInfo(15) { PageOffset = 0 }, null);
var msgs = msgsPage.Items;
foreach (var msg in msgs)
{
    Console.WriteLine(msg.Subject);
}
```
## **Create and Update a Folder**

To create a new folder, call the [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createfolder/#createfolder) method. This returns a [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo/) object, which can then be modified and updated using the [UpdateFolder()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatefolder/) method.


```csharp
var folderInfo = client.CreateFolder("FolderName");
folderInfo.DisplayName = "FolderAnotherName";
client.UpdateFolder(folderInfo);
```

## **Copy a Folder**

Use the [CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copyfolder/#copyfolder) method to copy a folder to a new parent location. This method requires the destination parent folder ID and the ID of the folder being copied.


```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// copy Folder2 to Folder1
client.CopyFolder(folderInfo1.ItemId, folderInfo2.ItemId);
```

## **Move and Delete a Folder**

- To move a folder, use the [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/movefolder/#movefolder) method which accepts newParentId and itemId. 
- To delete a folder, use the [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/delete/#delete) method and provide the folder’s ItemId.

```csharp
var folderInfo1 = client.CreateFolder("Folder1");
var folderInfo2 = client.CreateFolder("Folder2");
    
// move Folder2 to Folder1
client.MoveFolder(folderInfo1.ItemId, folderInfo2.ItemId);
    
// delete Folder1
client.Delete(folderInfo1.ItemId)
```

