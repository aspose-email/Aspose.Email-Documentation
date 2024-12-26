---
title: Read Outlook PST and Get Folders and Subfolders Information
ArticleTitle: Read Outlook PST and Get Folders and Subfolders Information
type: docs
weight: 20
url: /java/read-outlook-pst-and-get-folders-and-subfolders-information/
---

## **Aspose.Email - Read Outlook PST and Get Folders and Subfolders Information**
Aspose.Email for Java lets you read Microsoft Outlook PST files. You can load a PST file from disk or stream into an instance of the [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) class and get the information about its contents, for example folders, subfolders and messages.

After loading the PST file into the [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) class, you can get the information about the file display name, root folder, subfolders and messages count.

**Java**

{{< highlight java >}}

 // Load the Outlook PST file

PersonalStorage pst = PersonalStorage.fromFile(dataDir + "personalStorage.pst");

// Get the Display Name of the PST file

System.out.println("Display Name: " + pst.getDisplayName());

// Get the folders information

FolderInfoCollection folderInfoCollection = pst.getRootFolder().getSubFolders();

// Browse through each folder to display folder name and number of messages

for (int i = 0; i < folderInfoCollection.size(); i++)

{

    FolderInfo folderInfo = (FolderInfo) folderInfoCollection.get_Item(i);

    System.out.println("Folder: " + folderInfo.getDisplayName());

    System.out.println("Total items: " + folderInfo.getContentCount());

    System.out.println("Total unread items: " + folderInfo.getContentUnreadCount());

    System.out.println("-----------------------------------");

}

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}} 

For more details, visit [Read Outlook PST File and Get Folders and Subfolders Information](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}
