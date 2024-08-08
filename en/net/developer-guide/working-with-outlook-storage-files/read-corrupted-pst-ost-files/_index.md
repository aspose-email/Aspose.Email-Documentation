---
title: Read corrupted PST/OST files
type: docs
weight: 112
url: /net/read-corrupted-pst-ost-files/
---

Sometimes it may not be possible to read the PST/OST due to some issues. For example, some data blocks may be corrupted. In such cases, exceptions usually arise when calling the [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/), etc. methods. But individual messages or folders may remain undamaged in the storage.

## **Methods to find the item identifiers**

The following methods allow to find item identifiers in a hierarchical manner.

- [FindMessages(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - finds the identifiers of messages for the folder.
- [FindSubfolders(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - finds the identifiers of subfolders for the folder.

Identifiers obtained using the methods can be used to retrieve messages and folders.

> **_NOTE:_** It should be noted that despite its advantages, there are corrupted storages that cannot be read even using these methods.

## **PST file traversing**

The following code sample shows PST file traversing and extracting folders and messages. To get the list of identifiers use FindMessages and FindSubfolders methods. Then the identifier is passed to the [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) or [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) method to extract elements.

```csharp
using (var pst = PersonalStorage.FromFile(fileName))
{
    ExploreCorruptedPst(pst, pst.RootFolder.EntryIdString);
}

public static void ExploreCorruptedPst(PersonalStorage pst, string rootFolderId)
{
    var messageIdList = pst.FindMessages(rootFolderId);

    foreach (var messageId in messageIdList)
    {
        try
        {
            var msg = pst.ExtractMessage(messageId);
            Console.WriteLine( "- " + msg.Subject);
        }
        catch
        {
            Console.WriteLine("Message reading error. Entry id: " + messageId);
        }
    }

    var folderIdList = pst.FindSubfolders(rootFolderId);

    foreach (var subFolderId in folderIdList)
    {
        if (subFolderId != rootFolderId)
        {
            try
            {
                FolderInfo subfolder = pst.GetFolderById(subFolderId);
                Console.WriteLine(subfolder.DisplayName);
            }
            catch
            {
                Console.WriteLine("Message reading error. Entry id: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```
