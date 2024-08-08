---
title: Working with MapiTask in PST
type: docs
weight: 60
url: /net/working-with-mapitask-in-pst/
---


## **Adding MapiTask to PST**

The [Create a New PST File and Add Subfolders](https://docs.aspose.com/email/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) article shows how to create a PST file and add a subfolder to it. With Aspose.Email you can add [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) to the Tasks subfolder of a PST file that you have created or loaded. Below are the steps to add MapiTask to a PST:

1. Create a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) object.
2. Set the [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) properties using constructor and different methods.
3. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Create a pre-defined folder (Tasks) at the root of the PST file by accessing the Root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) and then add it to the tasks folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}
