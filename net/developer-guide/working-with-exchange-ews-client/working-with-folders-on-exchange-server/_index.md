---
title: Working with Folders on Exchange Server
type: docs
weight: 80
url: /net/working-with-folders-on-exchange-server/
---


## **Listing all Folders from Server**
Aspose.Email API provides the capability to connect to the Exchange Server and list all the folders and sub-folders. You can also retrieve all the sub-folders from each folder recursively. It also provides the capability to enumerate folders with paging from the Exchange client using Exchange Web Serice (EWS). This article shows how to retrieve all the sub-folders from the Exchange server and retrieve folders with pagination.

The following code snippet shows you how to List folders from Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListFoldersFromExchangeServer-ListFoldersFromExchangeServer.cs" >}}
## **Get Folder Type Information using EWS**
The [FolderType](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo/properties/foldertype) property provided by [ExchangeFolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfo) class can be used to get information about the type of the folder. This is as shown in the code sample below.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-GetFolderTypeInformationUsingEWS-GetFolderTypeInformationUsingEWS.cs" >}}
## **Enumerating Folders with Paging Support using EWS**
The following code snippet shows you how to use paging support using EWS.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-EnumeratMessagesWithPaginginEWS-EnumeratMessagesWithPaginginEWS.cs" >}}
## **Accessing Mailbox Custom Folders or Subfolders**
[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) lets developers access any custom folder or subfolder from the mailbox. The [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/folderexists/index) function of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) returns the URI of a specified custom folder/sub-folder, which can be used then to access the target folder. In the following example, a custom folder named "TestInbox", which is created under INBOX is accessed and all the messages are displayed from this custom folder. To perform this task, the following are the steps:

1. Initialize the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) object by providing valid credentials.
1. Access the default mailbox.
1. Access the parent folder, which is INBOX in this example. This parent folder can also be a custom folder itself.
1. Use [FolderExists()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/folderexists/index) to search the specified custom subfolder, for example "TestInbox". It will return the URI of "TestInbox".
1. Use this Uri to access all the messages in that custom folder.

The following code snippet shows you how to access mailbox custom folders or subfolders with EWS.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AccessCustomFolderUsingExchangeWebServiceClient-AccessCustomFolderUsingExchangeWebServiceClient.cs" >}}
## **Listing Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email's [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to read all public folders, and subfolders, and lists and download any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cs" >}}
## **Copy a Message to another Folder**
Aspose.Email API allows copying a message from one folder to another folder using the [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/copyitem) method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cs" >}}
## **Synching Folder Items**
Aspose.Email for .NET API's [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) provides the feature of syncing an Exchange folder for its contents. The [SyncFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/syncfolder/index) method exposed by the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) class can be used to perform folder sync information on a specified folder. The following code snippet shows you how to sync exchange folder information.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SynchronizeFolderItems-SynchronizeFolderItems.cs" >}}
## **Retrieving Permissions for Exchange Folders**
Users are assigned permissions to public folders on Exchange Server, which limits/determine the level of access a user has to these folders. The [ExchangeFolderPermission](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission) class provides a set of permission properties for Exchange folders such as the [PermissionLevel](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderpermission/properties/permissionlevel), whether they can [CanCreateItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/properties/cancreateitems), [DeleteItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangebasepermission/properties/deleteitems), and perform other tasks as specified by the permission properties. Permissions can be retrieved using the [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/getfolderpermissions) method of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient). This article shows how to retrieve the permissions applied to a public folder for all the users who have access to the shared folders.

To perform this task:

1. Initialize the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient).
1. Use the [ListPublicFolders](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/listpublicfolders) to get a list of all public folders
1. Retrieve the permissions associated with a folder using the [GetFolderPermisssions()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/getfolderpermissions) method

The following code snippet shows you how to use the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) class to retrieve permissions applied to a folder.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetrieveFolderPermissionsUsingExchangeWebServiceClient-RetrieveFolderPermissionsUsingExchangeWebServiceClient.cs" >}}
## **Creating Folders and Sub-Folders**
Aspose.Email API provides the capability to create folders in an Exchange mailbox. The [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/createfolder/index) method of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) can be used for this purpose. In order to create a folder in the Exchange server mailbox, the following steps can be used.

1. Create an instance of [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient).
1. Set the [UseSlashAsFolderSeparator](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/properties/useslashasfolderseparator) property as required. If set to **true**, the application will consider the "Slash" as folder separator and the subfolder will be created after the slash.
1. Use the [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/createfolder/index) method to create the folder.

The following code snippet shows you how to create folders and sub-Folders.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreateFoldersOnExchangeServerMailbox-CreateFoldersOnExchangeServerMailbox.cs" >}}
## **Backup Exchange Folders to PST**
It often so happens that users may want to take a backup of all or some of the mailbox folders. Aspose.Email provides the capability to take a backup of all or specified Exchange mailbox folders to a PST. This article describes taking backup of Exchange folders to a PST with sample code. In order to take the backup of Exchange server folders, the following steps may be followed.

1. Initiate the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient) with user credentials
1. Add the required folder's info to [ExchangeFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangefolderinfocollection)
1. User the client's [Backup](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/backup/index) method to export the folder's contents to PST

The following code snippet shows you how to backup exchange folders to PST.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeFoldersBackupToPST-ExchangeFoldersBackupToPST.cs" >}}
