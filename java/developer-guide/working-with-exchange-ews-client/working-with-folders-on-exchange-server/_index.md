---
title: Working with Folders on Exchange Server
type: docs
weight: 80
url: /java/working-with-folders-on-exchange-server/
---


## **Listing all Folders from Server**
Aspose.Email API provides the capability to connect to the Exchange Server and list all the folders and sub-folders. You can also retrieve all the sub-folders from each folder recursively. It also provides the capability to enumerate folders with paging from the Exchange client using Exchange Web Serice (EWS). This article shows how to retrieve all the sub-folders from the Exchange server and retrieve folders with pagination.

The following code snippet shows you how to List folders from Exchange Server.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    try {
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
        System.out.println("Downloading all messages from Inbox....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listSubFolders(client, folderInfo);
        }

        System.out.println("All messages downloaded.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void listSubFolders(IEWSClient client, ExchangeFolderInfo folderInfo) {
    // Create the folder in disk (same name as on IMAP server)
    System.out.println(folderInfo.getDisplayName());
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Get Folder Type Information using EWS**
The [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)) property provided by [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo) class can be used to get information about the type of the folder. This is as shown in the code sample below.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeFolderInfoCollection folderInfoCol = client.listSubFolders(client.getMailboxInfo().getRootUri());
for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCol) {
    switch (folderInfo.getFolderType()) {
    case ExchangeFolderType.Appointment:
        // handle Appointment
        break;
    case ExchangeFolderType.Contact:
        // handle Contact
        break;
    case ExchangeFolderType.Task:
        // handle Task
        break;
    case ExchangeFolderType.Note:
        // handle email message
        break;
    case ExchangeFolderType.StickyNote:
        // handle StickyNote
        break;
    case ExchangeFolderType.Journal:
        // handle Journal
        break;
    default:
        break;
    }
}
~~~
## **Enumerating Folders with Paging Support using EWS**
The following code snippet shows you how to use paging support using EWS.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());
int itemsPerPage = 5;
List<PageInfo> pages = new ArrayList<PageInfo>();
PageInfo pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
pages.add(pagedMessageInfoCol);
while (!pagedMessageInfoCol.getLastPage()) {
    pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
    pages.add(pagedMessageInfoCol);
}
pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
while (!pagedMessageInfoCol.getLastPage()) {
    client.listMessages(client.getMailboxInfo().getInboxUri());
}
~~~
## **Accessing Mailbox Custom Folders or Subfolders**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) lets developers access any custom folder or subfolder from the mailbox. The [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) function of [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) returns the URI of a specified custom folder/sub-folder, which can be used then to access the target folder. In the following example, a custom folder named "TestInbox", which is created under INBOX is accessed and all the messages are displayed from this custom folder. To perform this task, the following are the steps:

1. Initialize the IEWSClient object by providing valid credentials.
1. Access the default mailbox.
1. Access the parent folder, which is INBOX in this example. This parent folder can also be a custom folder itself.
1. Use folderExists() to search the specified custom subfolder, for example "TestInbox". It will return the URI of "TestInbox".
1. Use this Uri to access all the messages in that custom folder.

The following code snippet shows you how to access mailbox custom folders or subfolders with EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create ExchangeMailboxInfo, ExchangeMessageInfoCollection instance
ExchangeMailboxInfo mailbox = client.getMailboxInfo();
ExchangeMessageInfoCollection messages = null;
ExchangeFolderInfo subfolderInfo = new ExchangeFolderInfo();

// Check if specified custom folder exisits and Get all the messages info from the target Uri
ExchangeFolderInfo[] referenceToSubfolderInfo = { subfolderInfo };
client.folderExists(mailbox.getInboxUri(), "TestInbox", /* out */ referenceToSubfolderInfo);
subfolderInfo = referenceToSubfolderInfo[0];

// if custom folder exists
if (subfolderInfo != null) {
    messages = client.listMessages(subfolderInfo.getUri());

    // Parse all the messages info collection
    for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) messages) {
        String strMessageURI = info.getUniqueUri();
        // now get the message details using FetchMessage()
        MailMessage msg = client.fetchMessage(strMessageURI);
        System.out.println("Subject: " + msg.getSubject());
    }
} else {
    System.out.println("No folder with this name found.");
}
~~~
## **Listing Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email's [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to read all public folders, and subfolders, and lists and download any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Name: " + publicFolder.getDisplayName());
        System.out.println("Subfolders count: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Folder Name: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Call this method recursively for any subfolders
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Copy a Message to another Folder**
Aspose.Email API allows copying a message from one folder to another folder using the [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.



~~~Java
try {
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Synching Folder Items**
Aspose.Email for Java API's [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) provides the feature of syncing an Exchange folder for its contents. The [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)) method exposed by the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class can be used to perform folder sync information on a specified folder. The following code snippet shows you how to sync exchange folder information.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sync Folder Items");
client.send(message1);

MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sync Folder Items");
client.send(message2);

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
SyncFolderResult result = client.syncFolder(client.getMailboxInfo().getInboxUri(), null);
System.out.println(result.getNewItems().size());
System.out.println(result.getChangedItems().size());
System.out.println(result.getReadFlagChanged().size());
System.out.println(result.getDeletedItems().length);
~~~
## **Retrieving Permissions for Exchange Folders**
Users are assigned permissions to public folders on Exchange Server, which limits/determine the level of access a user has to these folders. The [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) class provides a set of permission properties for Exchange folders such as the [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), whether they can [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\)), and perform other tasks as specified by the permission properties. Permissions can be retrieved using the [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) method of [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). This article shows how to retrieve the permissions applied to a public folder for all the users who have access to the shared folders.

To perform this task:

1. Initialize the EWSClient.
1. Use the listPublicFolders to get a list of all public folders
1. Retrieve the permissions associated with a folder using the getFolderPermissions() method

The following code snippet shows you how to use the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to retrieve permissions applied to a folder.



~~~Java
String folderName = "DesiredFolderName";

// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeFolderInfoCollection folders = client.listPublicFolders();
ExchangeFolderPermissionCollection permissions = new ExchangeFolderPermissionCollection();

ExchangeFolderInfo publicFolder = null;
try {
    for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folders)
        if (folderInfo.getDisplayName().equals(folderName))
            publicFolder = folderInfo;

    if (publicFolder == null)
        System.out.println("public folder was not created in the root public folder");

    ExchangePermissionCollection folderPermissionCol = client.getFolderPermissions(publicFolder.getUri());
    for (ExchangeBasePermission perm : (Iterable<ExchangeBasePermission>) folderPermissionCol) {
        if (perm instanceof ExchangeFolderPermission)
            System.out.println("Permission is null.");
        else {
            ExchangeFolderPermission permission = (ExchangeFolderPermission) perm;

            System.out.println("User's primary smtp address: " + permission.getUserInfo().getPrimarySmtpAddress());
            System.out.println("User can create Items: " + permission.canCreateItems());
            System.out.println("User can delete Items: " + permission.getDeleteItems());
            System.out.println("Is Folder Visible: " + permission.isFolderVisible());
            System.out.println("Is User owner of this folder: " + permission.isFolderOwner());
            System.out.println("User can read items: " + permission.getReadItems());
        }
    }
    ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
    // Get the Permissions for the Contacts and Calendar Folder
    ExchangePermissionCollection contactsPermissionCol = client.getFolderPermissions(mailboxInfo.getContactsUri());
    ExchangePermissionCollection calendarPermissionCol = client.getFolderPermissions(mailboxInfo.getCalendarUri());
} finally {
    // Do the needfull
}
~~~
## **Creating Folders and Sub-Folders**
Aspose.Email API provides the capability to create folders in an Exchange mailbox. The [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) method of [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) can be used for this purpose. In order to create a folder in the Exchange server mailbox, the following steps can be used.

1. Create an instance of IEWSClient.
1. Set the UseSlashAsFolderSeparator property as required. If set to **true**, the application will consider the "Slash" as folder separator and the subfolder will be created after the slash.
1. Use the createFolder method to create the folder.

The following code snippet shows you how to create folders and sub-Folders.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String inbox = client.getMailboxInfo().getInboxUri();
String folderName1 = "EMAILNET-35054";
String subFolderName0 = "2015";
String folderName2 = folderName1 + "/" + subFolderName0;
String folderName3 = folderName1 + " / 2015";
ExchangeFolderInfo rootFolderInfo = null;
ExchangeFolderInfo folderInfo = null;

try {
    client.setUseSlashAsFolderSeparator(true);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName1);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName2);
} finally {
    ExchangeFolderInfo[] referenceToRootFolderInfo = { rootFolderInfo };
    boolean outRefCondition0 = client.folderExists(inbox, folderName1, /* out */ referenceToRootFolderInfo);
    rootFolderInfo = referenceToRootFolderInfo[0];
    if (outRefCondition0) {
        ExchangeFolderInfo[] referenceToFolderInfo = { folderInfo };
        boolean outRefCondition1 = client.folderExists(inbox, folderName2, /* out */ referenceToFolderInfo);
        folderInfo = referenceToFolderInfo[0];
        if (outRefCondition1)
            client.deleteFolder(folderInfo.getUri(), true);
        client.deleteFolder(rootFolderInfo.getUri(), true);
    }
}
~~~
## **Backup Exchange Folders to PST**
It often so happens that users may want to take a backup of all or some of the mailbox folders. Aspose.Email provides the capability to take a backup of all or specified Exchange mailbox folders to a PST. This article describes taking backup of Exchange folders to a PST with sample code. In order to take the backup of Exchange server folders, the following steps may be followed.

1. Initiate the IEWSClient with user credentials
1. Add the required folder's info to ExchangeFolderInfoCollection
1. User the client's backup method to export the folder's contents to PST

The following code snippet shows you how to backup exchange folders to PST.



~~~Java
String dataDir = "data/";
// Create instance of IEWSClient class by providing credentials
final String mailboxUri = "https://ews.domain.com/ews/Exchange.asmx";
final String domain = "";
final String username = "username";
final String password = "password";
NetworkCredential credential = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
ExchangeFolderInfo info = client.getFolderInfo(mailboxInfo.getInboxUri());
ExchangeFolderInfoCollection fc = new ExchangeFolderInfoCollection();
fc.addItem(info);
client.backup(fc, dataDir + "Backup_out.pst", BackupOptions.None);
~~~