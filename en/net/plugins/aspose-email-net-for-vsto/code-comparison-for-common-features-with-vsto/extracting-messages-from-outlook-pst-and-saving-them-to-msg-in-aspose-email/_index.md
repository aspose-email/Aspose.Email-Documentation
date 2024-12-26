---
title: Extracting Messages from Outlook PST and Saving them to MSG in Aspose.Email
ArticleTitle: Extracting Messages from Outlook PST and Saving them to MSG in Aspose.Email
type: docs
weight: 130
url: /net/extracting-messages-from-outlook-pst-and-saving-them-to-msg-in-aspose-email/
---


## **VSTO**
``` cs

 string pstFilePath = "sample.pst";

Outlook.Application app = new Application();

NameSpace outlookNs = app.GetNamespace("MAPI");

// Add PST file (Outlook Data File) to Default Profile

outlookNs.AddStore(pstFilePath);

MAPIFolder rootFolder = outlookNs.Stores["sample"].GetRootFolder();

// Traverse through all folders in the PST file

// TODO: This is not recursive

Folders subFolders = rootFolder.Folders;

foreach (Folder folder in subFolders)

{

	Items items = folder.Items;

	foreach (object item in items)

	{

		if (item is MailItem)

		{

			// Retrieve the Object into MailItem

			MailItem mailItem = item as MailItem;

			Console.WriteLine("Saving message {0} ....", mailItem.Subject);

			// Save the message to disk in MSG format

			// TODO: File name may contain invalid characters [\ / : * ? " < > |]

			mailItem.SaveAs(@"\extracted\" + mailItem.Subject + ".msg", OlSaveAsType.olMSG);

		}

	}

}

// Remove PST file from Default Profile

outlookNs.RemoveStore(rootFolder);

```
## **Aspose.Email**
``` cs

 string pstFilePath ="sample.pst";

// Create an instance of PersonalStorage and load the PST from file

using (PersonalStorage personalStorage = PersonalStorage.FromFile(pstFilePath))

{

	// Get the list of subfolders in PST file

	FolderInfoCollection folderInfoCollection = personalStorage.RootFolder.GetSubFolders();

	// Traverse through all folders in the PST file

	// TODO: This is not recursive

	foreach (FolderInfo folderInfo in folderInfoCollection)

	{

		// Get all messages in this folder

		MessageInfoCollection messageInfoCollection = folderInfo.GetContents();

		// Loop through all the messages in this folder

		foreach (MessageInfo messageInfo in messageInfoCollection)

		{

			// Extract the message in MapiMessage instance

			MapiMessage message = personalStorage.ExtractMessage(messageInfo);

			Console.WriteLine("Saving message {0} ....", message.Subject);

			// Save the message to disk in MSG format

			// TODO: File name may contain invalid characters [\ / : * ? " < > |]

			message.Save(@"\extracted\" + message.Subject + ".msg");

		}

```
## **Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772941)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Extract.Messages.from.PST.file.n.Save.in.MSG.Format.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Extract%20Messages%20from%20PST%20file%20n%20Save%20in%20MSG%20Format%20\(Aspose.Email\).zip)
