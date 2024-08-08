---
title: Get Folders Information from IMAP Mailbox
type: docs
weight: 10
url: /java/get-folders-information-from-imap-mailbox/
---

## **Aspose.Email - Get Folders Information from IMAP Mailbox**
Getting information about folders from an IMAP server is very easy with Aspose.Email. The listFolders() method of ImapClient returns an object of the ImapFolderInfoCollection that contains information about all the server folders. Iterate through this collection and get information about individual folders in a loop. The method is overloaded. You can pass a folder name as a parameter to get a list of subfolders.

**Java**

``` java

 ImapClient client = new ImapClient();

client.setHost("--server--"); //imap.secureserver.net,

client.setPort(993);

client.setUsername("--username--");

client.setPassword("--password--");

client.setSecurityOptions(SecurityOptions.Auto);

ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Iterate through the collection to get folder info one by one

for (ImapFolderInfo folderInfo:folderInfoColl)

{

	// Folder name

	System.out.println("Folder name is: " + folderInfo.getName());

	ImapFolderInfo folderExtInfo = client.listFolder(folderInfo.getName());

	// New messages in the folder

	System.out.println("New message count: " + folderExtInfo.getNewMessageCount());

	// Check whether its read only

	System.out.println("Is it readonly? " + folderExtInfo.getReadOnly());

	// Total number of messages

	System.out.println("Total number of messages: " + folderExtInfo.getTotalMessageCount());

}

```
## **Download Running Code**
Download **Get Folders Information from IMAP Mailbox** from any of the below mentioned social coding sites:

- [CodePlex](https://archive.codeplex.com/?p=asposeapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
